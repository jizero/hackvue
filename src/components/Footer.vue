<template>
<footer id="footer" class="k_foot">
        <div class="about_commerce">
          <a href="#none" class="link_commerce">
            <img src="https://t1.daumcdn.net/kstyle/m640/logo_commerce_190212.png" class="thumb_img" alt="kakaocommerce" />
          </a>
          <h2 class="screen_out">서비스 약관 및 정보</h2>
          <div class="info_policy">
            <a href="//buy.kakao.com/about/10/terms" class="link_policy" target="_blank">이용약관</a>
            <span class="ico_bar"></span>
            <a href="/info/shop" class="link_policy">사업자정보</a>
          </div>
        </div>
        <small
          class="desc_policy"
        >(주) 카카오커머스는 통신판매중개자로서 통신판매의 당사자가 아니며 상품의 주문, 배송 및 환불등과 관련한 의무와 책임은 각 판매자에게 있습니다.</small>
      </footer>
</template>

<style >

.k_foot {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    height: 233px;
    border-top: 1px solid #f5f5f5;
    font-size: 12px;
    background-color: #fafafa;
    z-index: 25;
}
.k_foot .about_commerce {
    overflow: hidden;
    max-width: 750px;
    margin: 0 auto;
    padding: 49px 20px 0;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
.k_foot .link_commerce {
    float: left;
    width: 110px;
}
.k_foot .info_policy {
    float: right;
}
.k_foot .desc_policy {
    display: block;
    max-width: 750px;
    margin: 0 auto;
    padding: 14px 20px 0;
    font-size: 12px;
    color: #a6a6a6;
    line-height: 17px;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    word-break: keep-all;
    word-wrap: break-word;
}
.k_foot .link_commerce .thumb_img {
    display: block;
    width: 100%;
}
.screen_out {
    overflow: hidden;
    position: absolute;
    width: 0;
    height: 0;
    line-height: 0;
    text-indent: -9999px;
}
</style>