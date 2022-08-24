<template>
    <view>
        <view class="head">
            <view @click="goBack" class="goBack">
                <image src="../../static/report/back01.png"></image>
            </view>
            <view class="head_title">举报</view>
        </view>
        <view class="type">
            请选择举报类型
        </view>
        <view class="content">
            <view class="content_text">
                反动政治
            </view>
            <view class="content_text">
                色情低俗
            </view>
            <view class="content_text">
                涉嫌诈骗
            </view>
            <view class="content_text">
                广告引流
            </view>
            <view class="content_text">
                骚扰谩骂
            </view>
            <view class="content_text">
                血腥暴力
            </view>
            <view class="content_text">
                违法行为
            </view>
            <view class="content_text">
                Ta是未成年
            </view>
            <view class="content_text">
                其他内容
            </view>
            <view class="content_text conten_last">
                微信账号异常
            </view>
        </view>
    </view>
</template>

<script>
    export default {
        data() {
            return {

            };
        },
        methods: {
            goBack() {
                uni.navigateBack({})
            }
        }
    }
</script>

<style lang="scss" scoped>
    page {
        background-color: #110F1C;
    }

    .head {
        margin: 0.625rem;
        color: #fff;
        display: flex;

        .goBack {
            padding-left: 0.625rem;

            image {
                width: 0.9375rem;
                height: 0.9375rem;
            }
        }

        .head_title {
            text-align: center;
            margin-left: 40%;
        }
    }

    .type {
        text-align: center;
        width: 5.6875rem;
        height: 0.75rem;
        font-size: 0.75rem;
        font-family: SourceHanSansSC-Medium, SourceHanSansSC;
        font-weight: 500;
        color: #999999;
        line-height: 1.125rem;
        padding: 0.625rem 0.8125rem;
    }

    .content {
        padding-top: 1.25rem;
        background-color: #110F1C;

        .content_text {
            margin: 0.625rem 1.25rem;
            padding: 0.3125rem 0;
            height: 1.875rem;
            color: #fff;
            font-size: 0.875rem;
            font-family: SourceHanSansSC-Medium, SourceHanSansSC;
            font-weight: 500;
            line-height: 1.3125rem;
            border-bottom: 0.0625rem solid RGB(39, 37, 50);
        }

        .conten_last {
            border-bottom: none;
        }
    }
</style>
