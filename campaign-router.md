# 랜딩 관리 스크립트 설치 가이드
키워드에 대응하고자 하는 랜딩 페이지에 아래의 코드를 수정하여 삽입합니다. 
```html
<script src="//pickme.taggers.io/js/helpers/pickme-campaign-router.js"></script>
<script>
  var onRouteFailed = function () {
    /*
      랜딩 스크립트에 오류가 발생했을시에 실행됩니다.
      오류시에 특수한 처리가 필요할시에 수정하여 주세요.
     */
    console.log('onRouteFailed');
  };

  try {
    let router = new PickmeCampaignRouter({
      mallName: '{{ 발급받은 쇼핑몰명 }}',
      campaignId: '{{ 발급받은 캠페인 ID }}',
      query: window.location.search
    });
    router.route(onRouteFailed);
  } catch (e) {
    onRouteFailed();
  }
</script>
```
* `{{ 발급받은 쇼핑몰명 }}` Taggers에서 발급해드린 쇼핑몰명을 입력합니다.
* `{{ 발급받은 캠페인 ID }}` Taggers의 키워드 랜딩 상품을 요청하셨을때에 발급해드린 캠페인 ID를 입력합니다.
