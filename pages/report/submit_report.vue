<template>
    <!-- 提交举报 -->
    <view>
        <view class="head">
            <view @click="goBack" class="goBack">
                <image src="../../static/report/back01.png"></image>
            </view>
            <view class="head_title">举报</view>
        </view>

        <view class="content">

        </view>
    </view>
</template>

<script>
    export default {
        data() {
            return {

            };
        }
    }
</script>

<style lang="scss" scoped>
    page {
        background-color: #110F1C;
    }

    .head {
        margin: 10px;
        color: #fff;
        display: flex;

        .goBack {
            padding-left: 10px;

            image {
                width: 15px;
                height: 15px;

            }
        }

        .head_title {
            text-align: center;
            margin-left: 40%;
        }
    }


    .content {
        margin-top: 10px;
        border-top: 1px dashed #ccc;
    }
</style>
