<template>
  <div class="container px-3 my-4">
    <Header/>
    <section class="site-home-scene scene-cases">
      <div class="inner-container">
        <h2 class="shc-title">Products</h2>
        <p class="shc-sub-title">상품 구매하기</p>
        <p class="shc-descriptions">획득한 RWT으로 원하는 상품을 구매해보세요!</p>
      </div>

      <div class="shop-list-row row" >
        <img src="@/assets/img2/product/Product1.png" alt class="photo6 col-md-3 col-xl-2 text-center p-4 pr-md-0">
        <div class="col-md-6 col-xl-7 py-md-4 px-4 pb-2">
          <div class="d-flex justify-content-start mb-1">
            <h5 class="flex-shrink-1 m-0"> Atypical 멤버들의친필 사인 폴라로이드 세트</h5>
          </div>
          <div style="margin-top: 20px;"><span class="t_dgray">{{products[0].text}}</span></div>
          <div style="margin-top: 10px;"><span class="t_dgray">{{products[0].thx}}</span></div>
        </div>
        <div class="d-flex col-md-3 col-xl-3 flex-md-column flex-wrap justify-content-md-center align-items-center pt-md-4 pb-4">
          <div class="text-big m-2" :class="{disabled: products[0].disabled}"><strong>{{products[0].price}} RWT</strong></div>
          <button class="button-normal" v-on:click="valid_check(0)" v-bind:class="{disabled: products[0].disabled}">{{products[0].buy}}</button>
        </div>
      </div>

      <div class="shop-list-row row">
        <img src="@/assets/img2/product/Product2.jpg" alt class="photo6 d-block col-md-3 col-xl-2 text-center p-4 pr-md-0">
        <div class="shop-list-content col-md-6 col-xl-7 py-md-4 px-4 pb-2">
          <div class="d-flex justify-content-start mb-1">
            <h5 class="flex-shrink-1 m-0"> Jorney 앨범 준비 과정 미공개 이미지 파일 세트 (Digital)</h5>
          </div>
          <div style="margin-top: 20px;"><span class="t_dgray">{{products[1].text}}</span></div>
          <div style="margin-top: 10px;"><span class="t_dgray">{{products[1].thx}}</span></div>
        </div>
        <div class="d-flex col-md-3 col-xl-3 flex-md-column flex-wrap justify-content-md-center align-items-center px-3 px-md-0 pt-md-4 pb-4">
          <div class="text-big m-2" :class="{disabled: products[1].disabled}"><strong>{{products[1].price}} RWT</strong></div>
          <button class="button-normal" v-on:click="valid_check(1)" v-bind:class="{disabled: products[1].disabled}">{{products[1].buy}}</button>
        </div>
      </div>
      
      <div class="shop-list-row row">
        <img src="@/assets/img2/product/Product3.png" alt class="photo6 d-block col-md-3 col-xl-2 text-center p-4 pr-md-0">
        <div class="shop-list-content col-md-6 col-xl-7 py-md-4 px-4 pb-2">
          <div class="d-flex justify-content-start mb-1">
            <h5 class="flex-shrink-1 m-0" > ‘블루베리’ 팬미팅 티켓 얼리버드 (2장)</h5>
          </div>
          <div style="margin-top: 20px;"><span class="t_dgray">{{products[2].text}}</span></div>
          <div style="margin-top: 10px;"><span class="t_dgray">{{products[2].thx}}</span></div>
        </div>
        <div class="d-flex col-md-3 col-xl-3 flex-md-column flex-wrap justify-content-md-center align-items-center px-3 px-md-0 pt-md-4 pb-4">
          <div class="text-big m-2" :class="{disabled: products[2].disabled}"><strong>{{products[2].price}} RWT</strong></div>
          <button class="button-normal" v-on:click="valid_check(2)" v-bind:class="{disabled: products[2].disabled}">{{products[2].buy}}</button>
        </div>
      </div>

      <div class="shop-list-row row">
        <img src="@/assets/img2/product/Product4.png" alt class="photo6 d-block col-md-3 col-xl-2 text-center p-4 pr-md-0">
        <div class="shop-list-content col-md-6 col-xl-7 py-md-4 px-4 pb-2">
          <div class="d-flex justify-content-start mb-1">
            <h5 class="flex-shrink-1 m-0" > ‘나나칸타빌레’ 한정판 굿즈 세트 ( 엽서 + 키링 + 티셔츠 )</h5>
          </div>
          <div style="margin-top: 20px;"><span class="t_dgray">{{products[3].text}}</span></div>
          <div style="margin-top: 10px;"><span class="t_dgray">{{products[3].thx}}</span></div>
        </div>
        <div class="d-flex col-md-3 col-xl-3 flex-md-column flex-wrap justify-content-md-center align-items-center px-3 px-md-0 pt-md-4 pb-4">
          <div class="text-big m-2" :class="{disabled: products[3].disabled}"><strong>{{products[3].price}} RWT</strong></div>
          <button class="button-normal" v-on:click="valid_check(3)" v-bind:class="{disabled: products[3].disabled}">{{products[3].buy}}</button>
        </div>
      </div>
    </section>
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
  data () {
    return {
      products: [
        {
          buy: '구매하기',
          disabled: false,
          text: 'Front Attack 멤버들의 폴라로이드 사진과 친필싸인이 들어있는 상품입니다. 멤버는 랜덤으로 선정되며 코팅처리가 되어있어 튼튼합니다.',
          thx: '',
          price: '300'
        },
        {
          buy: '구매하기',
          disabled: false,
          text: '공개되지않은 앨범 비하인드 컷 5장을 디지털 파일로 보내드립니다. 노트북, 패드, 휴대전화 등 배경화면으로도 사용하실 수 있도록 다양한 사이즈를 지원합니다.',
          thx: '',
          price: '700'
        },
        {
          buy: '구매하기',
          disabled: false,
          text: '팬미팅 얼리버드 티켓 2장입니다. 좌석을 선택하실 수 있습니다. 당일 얼리버드 티켓을 제시하시면, 간단한 간식과 담요를 제공하고 있습니다.',
          thx: '',
          price: '1000'
        },
        {
          buy: '구매하기',
          disabled: false,
          text: 'Bread N Jam 멤버들의 엽서와 티셔츠 그리고 직접 만든 D.I.Y 키링을 함께 드립니다!  키링은 선택하실 수 있으며 , 엽서와 티셔츠는 랜덤으로 제공됩니다.',
          thx: '',
          price: '1200'
        }
      ]
    }
  },
  computed: {
    walletAddress() {
      return this.config.walletAddress
    },
    mtSymbol() {
      return this.config.mt.symbol
    },
    stSymbol() {
      return this.config.st.symbol
    },
    apiKey() {
      return this.config.dapp.apiKey
    },
    txActionName() {
      return this.config.txActionName
    },
    userName() {
      return this.config.userName
    }
  },
  methods: {
    load() {
      if (!this.isLoggedIn) return;
      for(let productId = 0; productId < 4; productId++){
        this.axios.post(`/api/txAction/${this.txActionName.getOwner}`,{
          'from': this.walletAddress.user,
          'inputs': {
            '_index': productId
          }
        })
          .then((response) => {
            if (response.data.data.res[0] !== '') {
              this.products[productId].buy='구매 완료';
              this.products[productId].disabled='true';
              this.products[productId].thx=((response.data.data.res[0])+"님, 구매가 확정되었습니다.");    
            }
          })
          .catch(() => {
          })
      }
    },
    valid_check(productId){
      if (!this.isLoggedIn) {
        this.checkLoginAndRouteIfNeeded();
        return
      }
      if(this.products[productId].disabled) {
        this.$swal('Info', '이미 구매하셨습니다.', 'info')
        return
      }
      this.axios.get(`/api/getBalance/${this.walletAddress.user}`)
        .then((response) => {
          if((BigNumber(response.data.data.balance).div((BigNumber('10')).pow(18)) >= parseInt(this.products[productId].price))){
            this.purchase(productId);
          }
          else{
            this.$swal('Fail', '보유하신 RWT를 확인해주세요!', 'error')
          }
        })
        .catch(() => {
          this.$swal('Fail', '잔고 확인 실패', 'error')
        })
    },
    purchase(productId){
      this.axios.post(`/api/txAction/${this.txActionName.purchase}`,{
          'from': this.walletAddress.user,
          'inputs' : {
            'receiverAddress': this.walletAddress.pd,
            'valueAmount': this.products[productId].price + '000000000000000000',
          }
        })
        .then(() => {
          this.axios.post(`/api/txAction/${this.txActionName.setOwner}`,{
              'from': this.walletAddress.user,
              'inputs': {
                '_index': productId,
                '_name': this.userName
              }
          })
            .then(() => {
              this.$swal('Success', '구매에 성공하였습니다.', 'success')
              this.products[productId].buy='구매 완료';
              this.products[productId].disabled='true';
              this.axios.post(`/api/txAction/${this.txActionName.getOwner}`,{
                'from': this.walletAddress.user,
                'inputs': {
                  '_index': productId
                }
              })
                .then((response) => {
                  if (response.data.data.res[0] !== '') {
                    this.products[productId].thx=((response.data.data.res[0])+"님 구매가 확정되었습니다.");    
                  }
                })
                .catch(() => {
                  this.$swal('Fail', '구매 내역 불러오기에 실패했습니다. getOwner 함수를 확인해주세요.', 'error')
                })
            })
            .catch(() => {
              this.$swal('Fail', '구매 확정에 실패했습니다. setOwner 함수를 확인해주세요.', 'error')
            });
        })
        .catch(() => {
          this.$swal('Fail', '구매에 실패하였습니다. purchase 함수를 확인해주세요.', 'error')
        });
      
    }
  }
}
</script>

<style scoped>
  .portfolio-image {
    background-image: url('../assets/img2/detail/1.jpg');
  }
  .inner-container{
    padding-top: 80px !important;
  }
</style>
