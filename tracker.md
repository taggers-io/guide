# 추적 스크립트 설치 가이드

## 상품 상세 페이지
상품 상세 페이지에 아래의 코드를 수정하여 삽입합니다.
```html
<script>
window.pickme=window.pickme||[],function(e,c,r,t,i){e.pickme.tracker||(e.pickme.tracker=function(){(e.pickme.tracker.q=e.pickme.tracker.q||[]).push(arguments)},t=c.createElement("script"),i=c.getElementsByTagName("script")[0],t.async=1,t.defer=1,t.src=r,i.parentNode.insertBefore(t,i))}(window,document,"//pickme.taggers.io/js/helpers/pickme-tracker.js");
pickme.tracker('newTracker', '{{ 발급받은 쇼핑몰명 }}');

pickme.tracker('enableActivityTracking', 30, 30);
pickme.tracker('trackItemView', '{{ 상품 코드 }}');
</script>
```
1. newTracker
* `{{ 발급받은 쇼핑몰명 }}` Taggers에서 발급해드린 쇼핑몰명을 입력합니다.
2. enableActivityTracking
3. trackItemView
* `{{ 상품 코드 }}` 해당 페이지에서 조회한 상품 코드를 입력합니다.

## 구매 완료 페이지
구매 완료 페이지에 아래의 코드를 수정하여 삽입합니다.
```html
<script>
window.pickme=window.pickme||[],function(e,c,r,t,i){e.pickme.tracker||(e.pickme.tracker=function(){(e.pickme.tracker.q=e.pickme.tracker.q||[]).push(arguments)},t=c.createElement("script"),i=c.getElementsByTagName("script")[0],t.async=1,t.defer=1,t.src=r,i.parentNode.insertBefore(t,i))}(window,document,"//pickme.taggers.io/js/helpers/pickme-tracker.js");
pickme.tracker('newTracker', '{{ 발급받은 쇼핑몰명 }}');

pickme.tracker('addTrans', '{{ 주문 번호 }}', '{{ 총 주문 금액 }}');
pickme.tracker('addItem', '{{ 주문 번호 }}', '{{ 상품 코드 1 }}', '{{ 상품 가격 1 }}', '{{ 상품 갯수 1 }}');
pickme.tracker('addItem', '{{ 주문 번호 }}', '{{ 상품 코드 2 }}', '{{ 상품 가격 2 }}', '{{ 상품 갯수 2 }}');
pickme.tracker('addItem', '{{ 주문 번호 }}', '{{ 상품 코드 3 }}', '{{ 상품 가격 3 }}', '{{ 상품 갯수 3 }}');
pickme.tracker('trackTrans');
</script>
```
1. newTracker
* `{{ 발급받은 쇼핑몰명 }}` Taggers에서 발급해드린 쇼핑몰명을 입력합니다.
2. addTrans
* `{{ 주문 번호 }}` 구매 완료시 생성되는 주문 번호를 입력합니다.
* `{{ 총 주문 금액 }}` 해당 주문의 총 결제 금액을 입력합니다.
3. addItem (복수번 사용 가능)
* `{{ 주문 번호 }}` addTrans에서 사용된 `{{ 주문 번호 }}`의 값을 입력합니다.
* `{{ 상품 코드 }}` 구매한 상품의 코드를 입력합니다.
* `{{ 상품 가격 }}` 구매한 상품의 개당 가격을 입력합니다.
* `{{ 상품 갯수 }}` 해당 상품을 몇 개나 주문 했는지에 대한 갯수를 입력합니다.
4. trackTrans
