<template>
  <div>
    <Header/>
    <div class="position-relative pt-5 pb-4">
      <div v-if="idolId == '1'" class="portfolio-image detail-01" style="z-index: -1;"></div>
      <div v-else-if="idolId == '2'" class="portfolio-image detail-02" style="z-index: -1;"></div>
      <div v-else-if="idolId == '3'" class="portfolio-image detail-03" style="z-index: -1;"></div>
      <div v-else-if="idolId == '4'" class="portfolio-image detail-04" style="z-index: -1;"></div>
      <div v-else-if="idolId == '5'" class="portfolio-image detail-05" style="z-index: -1;"></div>
      <div v-else-if="idolId == '6'" class="portfolio-image detail-06" style="z-index: -1;"></div>
      <div class="pt-5 px-4 px-md-5">
        <div class="py-md-4 py-xl-5 mx-lg-5">
          <div class="portfolio-caption">
            <div v-if="idolId == '1'" class="text-tiny t_white font-weight-400">어떤 빵보다 부드러운 목소리,<br>어떤 잼보다 달콤한 목소리.<br>우리가 바로 브레드 앤 잼</div>
            <div v-else-if="idolId == '2'" class="text-tiny t_white font-weight-400">I<br>LIKE<br>THE VOICE OF<br>'H.I.M'</div>
            <div v-else-if="idolId == '3'" class="text-tiny t_white font-weight-400">보라색 사과<br>하늘을 헤엄치는 나무늘보<br>우리는 Atypical</div>
            <div v-else-if="idolId == '4'" class="text-tiny t_white font-weight-400">우리의 목소리는<br>어떤 악기든 될 수 있죠<br>노래하듯이, 나나 칸타빌레!</div>
            <div v-else-if="idolId == '5'" class="text-tiny t_white font-weight-400">LIFE IS A JOURNEY,<br>NOT A DESTINATION.</div>
            <div v-else-if="idolId == '6'" class="text-tiny t_white font-weight-400">냉동고를 준비하세요,<br> 당신의 고막이 녹아버릴지도 모르니까.<br> Morning Glory</div>
          </div>
        </div>
      </div>
    </div>
    <div class="container px-3 my-4">
      <h1 class="f30 font-weight-700" v-for="e in content" :key="e.id">
        <span v-if="e.id == idolId">{{e.name}}</span>
      </h1>
      <div class="flex">
        <div class="flex-box-70">
          <div class="f15 font-weight-400" v-for="e in content" :key="e.id">
            <p v-if="e.id == idolId">{{e.desc}}</p>
          </div>
          <div class="layout-guide-box mt-4">
            <p class="t_primary" style="margin-bottom:10px; line-height: 20px;"> 
              <span class="f13 font-weight-700">목표 금액</span> &nbsp;
              <span  v-for="e in content" :key="e.id">
                <span v-if="e.id == idolId">{{e.targetAmount}}</span>
              </span>
              <span class="f13 font-weight-700">펀딩기간</span> &nbsp;
              <span>24일</span>
            </p>
            <p class="font-weight-700" style="margin-bottom:5px;"> 목표금액이 모이면 데뷔에 가까워집니다.<br></p>
            <span>후원해주신 모든 분께 매주 관련 뉴스레터를 보내드립니다.</span>
          </div>
        </div>
        <div class="flex-box-40" style="margin-left: 80px;">
          <div v-for="e in content" :key="e.id">
            <strong class="t_dgray f15 font-weight-400" v-if="e.id == idolId">{{e.message}}</strong>
          </div>
          <div>
            <strong id="money" class="f24 font-weight-700 mb4" v-bind:value="database">{{database.money}}<span class="f17 font-weight-700">&nbsp;원 펀딩</span></strong>
          </div>
          <div>
            <strong id="money" class="f24 font-weight-700 mb4" v-bind:value="database">{{database.people}}<span class="f17 font-weight-700">&nbsp; 명의 서포터</span></strong>
          </div>
          <div class="flex" style="margin-top: 15px;">
            <button type="submit" class="button-submit flex-box-80" style="font-weight:400 !important;" v-on:click="fund()">프로젝트 후원하기</button>
            <button type="submit" class="button-normal flex-box-20" v-bind:value="database" style="margin-left: 10px;" v-on:click="like()">
              <i class="fa fa-thumbs-up"></i>&nbsp;{{database.like}}</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from '@/components/header'
import MixinConfig from '@/components/mixins/MixinConfig'

export default {
  mixins: [MixinConfig],
  components: {
    Header,
  },
  data () {
    return {
      content: [
        {
          id: '1',
          name: '블루베리',
          message: '블루베리 데뷔 응원 프로젝트에 참여해보세요!',
          targetAmount: '10,000,000원 ㅣ ',
          desc: `‘BLUEBERRY'는 래퍼 블루와 비트메이커 허클베리로 구성된 남성 래퍼 듀오 그룹이다. 현재 소속사인 STICKY 엔터테인먼트와 계약하기 전부터 언더그라운드에서 유명했던 뮤지션들로 데뷔 전 발매한 믹스테이프가 판매량 만장을 넘어 화제가 된 적이 있다. 뛰어난 실력과 더불어 고등학생 시절 인터넷 얼짱으로도 올라왔을 정도의 외모 덕분에 아이돌 못지 않은 팬덤을 자랑한다. 블루의 중저음 목소리와 허클베리의 세련되고 신선한 비트가 잘 어우러져 하나의 음악을 만들어내는게 포인트다. `,
          database: {
            money: '7700000',
            people: '770',
            like: '1129'
          }
        },
        {
          id: '2',
          name: 'H.I.M.',
          message: 'H.I.M. 월드투어 프로젝트에 참여해보세요!',
          targetAmount: '100,000,000원 ㅣ ',
          desc: `2015년 3월 정규 1집 '1992'로 데뷔하자마자 각종 음원 사이트에서 앨범 전곡을 차트인 시켰던 괴물신인 'H.I.M.'! 감미로운 음색을 지닌 R&B 보컬로 개인 앨범뿐만 아니라 <미로>, <마이 페이지>, <투명우산> 등 수많은 인기 드라마의 OST 앨범에도 참여하여 '오스트남', '오공(오스트공무원)'이라는 별명을 가지고 있다. 얼마 전 한국을 시작으로 중국, 일본, 대만 등 아시아 7개국의 투어 콘서트를 마쳤고, 오는 5월 미국, 캐나다, 영국, 프랑스 등에서 단독 콘서트를 열어 세계 곳곳의 팬들과 만남을 가질 예정이다. `,
          database: {
            money: '256250000',
            people: '256250',
            like: '256'
          }
        },
        {
          id: '3',
          name: 'Atypical',
          message: 'Atypical 쇼케이스 응원 프로젝트에 참여해보세요!',
          targetAmount: '3,000,000원 ㅣ ',
          desc: `‘Atypical'은 케이시, 이지, 페이로 구성된 여성 아크로바틱 댄스 그룹이다. 당당하고 신인답지 않은 여유로움이 매력적이다. 그룹명 'Atypical'은 '이례적인'이라는 사전적 의미를 가지고 있으며 이 그룹명은 리더 케이시가 키, 혈액형, 입맛, 핸드폰 기종, 옷 입는 스타일, 이상형 등 어느 것 하나 공통점이 없는 멤버들이 특이해서 지은 이름이라고 한다. 작년 12월 소속사 유튜브 채널에 올라온 아크로바틱 안무영상으로 큰 화제를 불러 모았으며, 이후 영상 속에서 멤버들이 입었던 트레이닝복 브랜드와 광고모델로 계약을 하여 데뷔 전부터 승승장구하고 있는 그룹이다. `,
          database: {
            money: '600000',
            people: '60',
            like: '38'
          }
        },
        {
          id: '4',
          name: '나나 칸타빌레',
          message: '나나 칸타빌레 오카리나 제작 프로젝트에 참여해보세요!',
          targetAmount: '70,000,000원 ㅣ ',
          desc: `'나나 칸타빌레'는 오드리와 베스로 구성되어 있는 싱어송라이팅 여성 인디 듀오다. 피아노와 기타, 우쿨렐레, 캐스터네츠, 멜로디언 등 다양한 악기들과 무대를 꾸리는게 특징이다. 따뜻하게 위로해주는 가사와 과한 기교 없이 잔잔한 멜로디로 '나나 칸타빌레의 장르는 힐링.'이라는 말이 있으며, 특히 2, 30대 청춘들에게 인기가 많다. 콘서트 때마다 무대에 올라오는 악기들을 미대언니 출신 오드리가 직접 커스텀하는게 특이한데, 굿즈로 내달라는 팬들의 성화에 못 이겨 이번 전국투어 때 오드리와 베스가 함께 디자인 한 오카리나를 굿즈로 발매할 예정이다. `,
          database: {
            money: '41300000',
            people: '4130',
            like: '9718'
          }
        },
        {
          id: '5',
          name: 'Jorney',
          message: 'Journey 두 번째 정규앨범 제작 프로젝트에 참여해보세요!',
          targetAmount: '5,000,000원 ㅣ ',
          desc: `'Jorney'는 대학교 재학시절 밴드 동아리 친구들끼리 사회에 나와 다시 결성한 혼성 밴드 그룹이다. 우연히도 멤버들 모두 이름에 J가 들어가서 그룹 이름도 J로 시작하는 가장 멋진 단어로 지었다고 한다. 멤버 구성은 리더와 기타를 맡고 있는 조, 드럼 이준, 보컬 지수, 베이스와 서브보컬 줄라이, 키보드 제키로 되어있다. 첫 번째 정규 앨범이 발매된 후 여러 음악 평론가들에게 '한국의 Coldplay'라는 호평을 받았으며, 대표곡으로는 'Summer Breeze'와 'MARS'가 있다.`,
          database: {
            money: '2850000',
            people: '285',
            like: '111'
          }
        },
        {
          id: '6',
          name: 'MAX',
          message: 'MAX 북미 투어 DVD 프로젝트에 참여해보세요!',
          targetAmount: '5,000,000원 ㅣ ',
          desc: `보컬, 랩, 작사·작곡, 뭐든지 잘하는 만능 엔터테이너 MAX. 매력적인 허스키한 목소리와 알 수 없는 강인한 이미지가 돋보이는 싱어송라이터다. Adele, The Weekend, Taylor Swift 등 해외 유명 아티스트들과 함께 작업하기도 하였고, 여러 해외 에이전시에서 러브콜을 받고 있는 월드스타다. 월드스타라는 수식어가 무색하지 않게 두 차례 진행한 월드투어에서 무려 전석매진이라는 놀라운 성적표를 거두기도 했다. 앞으로 많은 대중들에게 사랑받을 아티스트로 성장할 것이라는 평가가 계속해서 이어지고 있다.`,
          database: {
            money: '5350000',
            people: '535',
            like: '761'
          }
        },
      ]
    }
  },
  computed: {
    walletAddress() {
      return (this.config || {}).walletAddress
    },
    apiKey() {
      return ((this.config || {}).dapp || {}).apiKey
    },
    txActionName() {
      return (this.config || {}).txActionName
    },
    userName() {
      return (this.config || {}).userName
    },
    idolId() {
      return this.$route.params.idolId
    },
    database() {
      return (this.content[parseInt(this.idolId) - 1] || {}).database
    }
  },
  methods: {
    load() {
      if (!this.isLoggedIn) return;
      this.axios.get(`https://api.luniverse.io/scan/v1.0/chains/5300575914426995782/accounts/${this.walletAddress.user}/transfer-events?limit=25`)
        .then((response) => {
          var l = parseInt(this.database.like.replace(/,/g,""));
          var p = parseInt(this.database.people.replace(/,/g,""));
          var m = parseInt(this.database.money.replace(/,/g,""));
          const transferEvents = response.data.data.transferEvents.items
          const filteredEvents = transferEvents.filter(valid => {
            const res = valid.hasOwnProperty('tokenContractAddress') && valid.tokenContractAddress.startsWith('0x')

            return res
          })
          filteredEvents.forEach(tx => {
            if(tx.value === '100000000000000000000'){
              l = l + 1;
            }
            else if(tx.value === '1000000000000000000000'){
              p = p + 1;
              m = m + 10000;
            }
          })
          l = l.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
          this.database.like = l;
          p = p.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
          this.database.people = p;
          m = m.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
          this.database.money = m;
        })
        .catch(() => {
        })
    },
    like(){
      if (!this.isLoggedIn) {
        this.checkLoginAndRouteIfNeeded();
        return;
      }
      let n = parseInt(this.database.like.replace(/,/g,"")); //,지운다
      this.axios.post(`/api/txAction/${this.txActionName.like}`,{ 
          'from': this.walletAddress.pd,
          'inputs' : {
            'receiverAddress': this.walletAddress.user,
            'valueAmount': '100000000000000000000'
          }
      })
        .then(() => {
          this.$swal('Success', '좋아요를 눌러주셔서 감사합니다!\n100RWT를 드려요!', 'success')
          n = n + 1;
          n = n.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
          this.database.like=n;
        })
        .catch(() => {
          this.$swal('Error', '좋아요에 실패했습니다!', 'error')
        });
    },
    fund(){
      if (!this.isLoggedIn) {
        this.checkLoginAndRouteIfNeeded();
        return;
      }
      let m = parseInt(this.database.money.replace(/,/g,""));
      let p = parseInt(this.database.people.replace(/,/g,""));
      this.axios.post(`/api/txAction/${this.txActionName.funding}`,{
            'from': this.walletAddress.pd,
            'inputs' : {
              'receiverAddress': this.walletAddress.user,
              'valueAmount': '1000000000000000000000'
            }
        })
        .then(() => {
          this.$swal('Success', '10,000원이 펀딩되었습니다.\n1,000RWT를 드려요!', 'success')
          m = m + 10000;
          m = m.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
          this.database.money=m;
          p = p + 1;
          p= p.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
          this.database.people=p;
        })
        .catch(() => {
          this.$swal('Fail', 'Fund에 실패했습니다!', 'error')
        });
    },
  }
}
</script>

