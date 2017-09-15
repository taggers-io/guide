# 픽미 검색 페이지 설치 가이드

## Client 설치
페이지를 하나 생성한 후 아래의 코드를 수정하여 입력합니다.
```html
<!doctype html>
<html lang="ko">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=yes">
</head>
<body style="margin: 0;">
  <div id="js-pickme-searcher-container"></div>
  <script>
    /* fallback generator */
    (function(e,n,c,t){var a=function(){name=e.replace(/[\[]/,"\\[").replace(/[\]]/,"\\]");var n=new RegExp("[\\?&]"+name+"=([^&#]*)"),c=n.exec(location.search);return null===c?"/":decodeURIComponent(c[1].replace(/\+/g," "))};n[c]=function(){t.location=a()}})
      .call(window,"fallback-url",window,"fallback",window.parent);
    /* installer */
    (function(e,n,c,t){var a=!1,o=function(){a||c&&c()},r=function(e,n){var c=document.createElement("SCRIPT"),t=document.getElementsByTagName("SCRIPT")[0];c.src=e,c.onload=n,t.parentNode.insertBefore(c,t)},i=function(){a=!0,t&&t()};setTimeout(o,n),r(e,i)})
      .call(window,"//static.pickme.taggers.io/js/helpers/pickme-iframe-client-manager.js",{{ timeout }},window.fallback,function(){
        PickmeIframeClientManager.install({
            container: document.getElementById('js-pickme-searcher-container'),
            mallName: '{{ 발급받은 쇼핑몰명 }}',
            searcherId: {{ 발급받은 검색기 ID }},
        });
      });
  </script>
</body>
</html>
```
* `{{ timeout }}` 검색 페이지를 로딩할 때 기다릴 최대 시간을 입력합니다.(단위: ms, ※ 1초 = 1000ms)
* `{{ 발급받은 쇼핑몰명 }}` Taggers에서 발급해드린 쇼핑몰명을 입력합니다.
* `{{ 발급받은 검색기 ID }}` Taggers에서 발급해드린 검색기 ID를 입력합니다.

## Host 설치
픽미 검색 도구를 설치하시고 싶으신 위치에 아래의 코드를 수정하여 삽입합니다.
```html
<div id="js-pickme-container">
  <script>
    /* iframe injector */
    (function(e,n,c){var t=document.createElement("IFRAME");t.id=n,t.frameBorder=0,t.setAttribute("data-base-url",c),document.querySelector(e).appendChild(t)})
      .call(window,"#js-pickme-container","js-pickme-component","{{ Client 주소 }}");
    /* fallback generator */
    (function(e,n,c,t){var a=function(){name=e.replace(/[\[]/,"\\[").replace(/[\]]/,"\\]");var n=new RegExp("[\\?&]"+name+"=([^&#]*)"),c=n.exec(location.search);return null===c?"/":decodeURIComponent(c[1].replace(/\+/g," "))};n[c]=function(){t.location=a()}})
      .call(window,"fallback-url",window,"fallback",window);
    /* installer */
    (function(e,n,c,t){var a=!1,o=function(){a||c&&c()},r=function(e,n){var c=document.createElement("SCRIPT"),t=document.getElementsByTagName("SCRIPT")[0];c.src=e,c.onload=n,t.parentNode.insertBefore(c,t)},i=function(){a=!0,t&&t()};setTimeout(o,n),r(e,i)})
      .call(window,"//static.pickme.taggers.io/js/helpers/pickme-iframe-host-manager.js",{{ timeout }},window.fallback,function(){
        new PickmeIframeHostManager({
          iframe:document.querySelector("#js-pickme-component")
        }).install()
      });
  </script>
  <style>
    #js-pickme-component{min-width:100%;min-height:100%;width:1px;height:1px;}
  </style>
</div>
```
* `{{ Client 주소 }}` 상단의 "Client 설치"에서 설치한 주소를 입력합니다.
* `{{ timeout }}` 검색 페이지를 로딩할 때 기다릴 최대 시간을 입력합니다.(단위: ms, ※ 1초 = 1000ms)
