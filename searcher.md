# 픽미 검색 페이지 설치 가이드

## 기본 설치
픽미 검색 도구를 페이지에 설치하시고 싶으신 위치에 아래의 코드를 수정하여 삽입합니다.
```html
<div id="js-pickme-searcher-container">
  <script src="//pickme.taggers.io/js/helpers/pickme-searcher-loader.js"></script>
  <script>
    var redirectUrlIfError = '/';
    try {
      var loader = new PickmeSearcherLoader({
        container: document.getElementById('js-pickme-searcher-container'),
        mallName: '{{ 발급받은 쇼핑몰명 }}',
        redirectUrlIfError: redirectUrlIfError,
      });
      loader.load();
    } catch (e) {
      window.location.href = redirectUrlIfError;
    }
  </script>
</div>
```
* `{{ 발급받은 쇼핑몰명 }}` Taggers에서 발급해드린 쇼핑몰명을 입력합니다.

## 충돌 처리
> 검색기의 속도를 최적화 하기 위하여 모든 데이터를 동적으로 불러오고 있습니다.
> 이에 따라서 a태그의 href속성에 #(해시태그)를 이용한 경우에는 우회 처리가 필요합니다.
### 우회 방법
#### '상단으로 가기' 목적으로 사용된 경우
```html
<script>
  var onJQueryLoaded = function ($) {
    var bypassScrollToTop = function (event) {
      window.scrollTo(0, 0);
      event.preventDefault();
    };
    <!-- 쇼핑몰의 jQuery의 버전이 1.7 이하일 경우 -->
    $('{{ jQuery selector }}').live('click', bypassScrollToTop);
    <!-- 쇼핑몰의 jQuery의 버전이 1.7 초과일 경우 -->
    $('{{ jQuery selector }}').on('click', bypassScrollToTop);
  };

  var deferUntilJQueryLoaded = function (afterLoaded) {
    if (window.jQuery) {
      afterLoaded(window.jQuery);
    } else {
      setTimeout(function () {
        deferUntilJQueryLoaded(afterLoaded);
      }, 100);
    }
  };
  deferUntilJQueryLoaded(onJQueryLoaded);
</script>
```
* `{{ jQuery selector }}` 우회할 element의 selector를 입력합니다. (ex. a[href^="#"])

#### 이외의 목적으로 사용된 경우
Taggers 개발팀에 문의 부탁드립니다.
