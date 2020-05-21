<template>
  <div>
    <Header/>
    <div class="pt-5">
      <div class="mypage-img my-img"></div>
      <div class="py-5">
        <div class="wrapper py-xl-5">
          <div class="portfolio-caption">
            <div class="portfolio-caption t_white font-weight-500"><div class="h1 mb4">{{username}}</div></div>
            <div class="portfolio-caption t_white font-weight-500">{{balance}} <span class="h1 mb4">RWT</span></div>
          </div>
        </div>
      </div>
    </div>
    <div class="container px-3">
      <div class="row justify-content-between">
        <div class="mb-3" style="margin-top: 3rem;">
          <h3>History</h3>
        </div>
        <table class="tbl">
            <colgroup>
            <col style="width:30%">
            <col style="width:10%">
            <col style="width:10%">
            <col style="width:20%">
          </colgroup>
          <thead>
            <tr>
              <th scope="col">일시</th>
              <th scope="col">송신자</th>
              <th scope="col">수신자</th>
              <th scope="col">금액</th>
            </tr>
          </thead>
          <tbody>
            <tr v-bind:key="`${i}`" v-for="(history, i) in History">
              <td scope="row"><time datetime="">{{history.time}}</time></td>
              <td scope="row">{{history.from}}</td>
              <td scope="row">{{history.to}}</td>
              <td scope="row" v-bind:style="{color: history.from === 'pd' ? '#00B580' : '#F14E4E'}">{{convertReadableNum(history.value)}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import Header from '@/components/header'
import BigNumber from 'bignumber.js'
import MixinConfig from '@/components/mixins/MixinConfig'

export default {
  mixins: [MixinConfig],
  components: {
    Header,
  },
  mounted() {
    this.load()
  },
  data() {
    return {
      balance: 0,
      historyFilter: undefined,
      History: [
      ]
    }
  },
  computed: {
    walletAddress() {
      return (this.config || {}).walletAddress
    },
    mtSymbol() {
      return ((this.config || {}).mt || {}).symbol
    },
    stSymbol() {
      return ((this.config || {}).st || {}).symbol
    },
    apiKey() {
      return ((this.config || {}).dapp || {}).apiKey
    },
    username() {
      return (this.config || {}).userName ? this.config.userName + ' 님의 지갑' : '지갑'
    },
  },
  methods: {
    load() {
      if (!this.isLoggedIn) return;
      this.axios.get(`/api/getBalance/${this.walletAddress.user}`)
        .then((response) => {
          this.balance = response.data.data.balance;
          this.balance = (BigNumber(this.balance)).div((BigNumber('10')).pow(18));
          // 블록체인에서 토큰을 표기하는 최소단위 Decimal에서 10^18 지워줌
        })
        .catch(() => {
          this.balance = 0;
        });
      
      this.axios.get(`https://api.luniverse.io/scan/v1.0/chains/5300575914426995782/accounts/${this.walletAddress.user}/transfer-events?limit=25`)
        .then((response) => {
          this.History = []
          const transferEvents = response.data.data.transferEvents.items
          const filteredEvents = transferEvents.filter(valid => {
            let res = valid.hasOwnProperty('tokenContractAddress') && valid.tokenContractAddress.startsWith('0x')

            return res
          })
          filteredEvents.forEach(tx => {
            const createdAt = this.$moment.unix(tx.timestamp).format("MM/DD/YYYY, h:mm:ss a");
            const from = tx.from === this.walletAddress.user ? this.config.userName : 'pd'
            const to = tx.to === this.walletAddress.pd ? 'pd' : this.config.userName

            this.History.push({
              time: createdAt,
              value: tx.value,
              from,
              to,
            })
          })
        })
        .catch(() => {
        })
    },
    applyHistoryFilter() {
      const now = this.$moment.utc(new Date())
      localStorage.setItem('historyFilter', now);
      this.$swal('Success', '필터 적용이 완료되었습니다.', 'success')
    },
    removeHistoryFilter() {
      localStorage.removeItem('historyFilter')
      this.$swal('Success', '필터 해제가 완료되었습니다.', 'success')
    },
    convertReadableNum(val) {
      return val.substring(0, val.length - 18)
    }
  }
}
</script>