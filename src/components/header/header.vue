<template>
    <div class="header">
         <div class="content-wrapper">
            <div class="avatar">
                <img width="64" height="64" :src="seller.avatar" />
            </div>
            <div class="content">
                <div class="title">
                    <span class="brand"></span>
                    <span class="name">{{seller.name}}</span>
                </div>
                <div class="description">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
                <div class="support" v-if="seller.supports">
                    <span class="icon" :class="classMap[1]"></span>
                    <span class="text">{{seller.supports[0].description}}</span>
                </div>
            </div>
            <div class="support-count" @click="showDetail">
                <span class="count">3个</span>
            </div>
        </div>
        <div class="bulletin-wrapper" @click="showDetail">
            <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
        </div>
        <div class="background">
            <img :src="seller.avatar" width="100%" height="100%">
        </div>
        <div class="detail" v-show="detailShow">
            <div class="detail-wrapper clearfix">
                 <div class="detail-main">
                    <h1 class="name">荆州蒸菜</h1>
                    <div class="star-wrapper">
                        <star :size="48" :score="4.2" ></star>
                    </div>
                    <div class="title">
                        <div class="line"></div>
                        <div class="text">优惠信息</div>
                        <div class="line"></div>
                    </div>
                 </div>
            </div>
            <div class="detail-close" @click="showDetail"><i>X</i></div>
        </div>
    </div>
</template>

<script>
import star from "../star/star";
import data from "../goods/data";
export default {
    data() {
     return {
        detailShow: false
     }
    },
    methods: {
        showDetail() {
            this.detailShow = !this.detailShow
        }
    },
    props: {
    },
    created(){
    	this.seller = data.seller;
        this.classMap = ['decrease','discound','guarantee']
    },
    components: {
        star
    }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import "../../assets/stylus/mixin"
    .header
        position: relative
        overflow: hidden
        color: #fff
        background: rgba(7, 12, 27, 0.5)
        .content-wrapper
            position: relative
            padding:24px 12px 18px 24px
            font-size: 0
            .avatar
                display: inline-block
                vertical-align: top
                img
                    border-radius: 2px
            .content
                display: inline-block
                margin-left: 16px
                .title
                    margin: 2px 0 8px 0
                    .brand
                        display: inline-block
                        vertical-align: top
                        width: 30px
                        height: 18px
                        background: url("brand@2x.png");
                        background-size: 30px 18px
                        background-repeat: no-repeat
                    .name
                        margin-left: 6px
                        font-size: 16px
                        line-height: 18px
                        font-weight: bold
                .description
                    margin-bottom: 10px
                    line-height: 12px
                    font-size: 12px
                .support
                    .icon
                        display: inline-block
                        vertical-align: top
                        width: 18px
                        height: 12px
                        margin-right: 4px
                        background-size: 18px 18px
                        background-repeat: no-repeat
                        &.decrease
                            background: url("decrease_1@2x.png")
                            background-size: 100% 100%
                        &.discound
                            background: url("discount_1@2x.png")
                            background-size: 100% 100%
                        &.guarantee
                            background: url("guarantee_1@2x.png")
                            background-size: 100% 100%
                    .text
                        line-height: 12px
                        font-size: 10px
            .support-count
                position: absolute
                right: 12px
                bottom: 14px
                padding: 0 8px
                height: 24px
                line-height: 24px
                border-radius: 14px
                background: rgba(0, 0, 0, 0.2)
                text-align: center
                .count
                    font-size: 10px
        .bulletin-wrapper
            height: 28px
            line-height: 28px
            padding: 0 22px 0 12px
            white-space: nowrap
            overflow: hidden
            text-overflow: ellipsis
            background: rgba(7, 17, 27, 0.2)
            .bulletin-title
                display: inline-block
                vertical-align: top
                margin-top: 8px
                width: 22px
                height: 12px
                bg-image("bulletin")
                background: url("bulletin@2x.png")
                background-size: 22px 12px
                background-repeat: no-repeat
            .bulletin-text
                vertical-align: top
                margin: 0 4px
                font-size: 10px
        .background
            position: absolute
            top: 0
            left: 0
            width: 100%
            heigth: 100%
            z-index: -1
            filter: blur(10px)
        .detail
            position: fixed
            z-index: 100
            top: 0
            left: 0
            width: 100%
            height: 100%
            overflow: auto
            background: rgba(7, 17, 27, 0.8)
            .detail-close
                position: relative
                width: 32px
                height: 32px
                margin: -64px auto 0 auto
                clear: both
                font-size: 32px
            .detail-wrapper
                width: 100%
                min-height: 100%
                width: 100%
                .detail-main
                    margin-top: 64px
                    padding-bottom: 64px
                    .name
                        line-height: 16px
                        text-align: center
                        font-size: 16px
                        font-weight: 700
                    .star-wrapper
                        margin-top: 18px
                        padding: 2px 0
                        text-align: center
                    .title
                        display: flex
                        width: 80%
                        margin: 30px auto 24px auto
                        .line
                            flex: 1
                            position: relative
                            top: -6px
                            border-bottom: 1px solid rgba(255, 255, 255, 0.2)
                        .text
                            padding: 0 12px
                            font-size: 14px
</style>