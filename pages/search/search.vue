<template>
    <view>
        <view class="head">
            <view @click="goBack" class="goBack">
                <image src="../../static/report/back01.png"></image>
            </view>
            <view class="u_search">
                <u-search :showAction="true" actionText="搜索" :animation="false" v-model="keyword" bgColor="#343345"
                    height="26" maxlength="30" :clearabled="true">
                </u-search>
            </view>
        </view>
        <view class="content">
            <view class="content_text">
                搜索发现
            </view>
            <view class="search_history">
                这一秒你在想什么
            </view>
            <view class="line"> </view>
            <view class="popular">
                热门话题
            </view>
            <view class="topiclist">
                <view class="topic" v-for="item in 5">
                    <view class="">
                        <img src="../../static/search/logo.png" alt="">
                    </view>
                    <view class="">
                        活成自己喜欢的样子
                    </view>
                    <view class="">
                        <view>
                            <img src="../../static/search/heat.png" mode=""></image>
                        </view>
                        <view class="">
                            79219
                        </view>
                    </view>

                </view>
            </view>
        </view>


    </view>
</template>

<script>
    export default {
        data() {
            return {
                keyword: ''
            };
        }
    }
</script>

<style lang="scss" scoped>
    page {
        background-color: #110F1C;
        color: #fff;
    }

    .head {
        margin: 0.625rem;
        color: #fff;
        display: flex;

        .goBack {
            margin-top: 0.3125rem;
            padding-left: 0.625rem;

            image {
                width: 0.9375rem;
                height: 0.9375rem;
            }
        }

        .u_search {
            margin-left: 1.25rem;
            width: 18.75rem;
        }

        /deep/ .u-search__action[data-v-0a306a29] {
            color: #fff;
        }
    }

    .content {
        margin: 1.25rem;

        .content_text {
            font-size: 0.875rem;
            font-family: SourceHanSansSC-Medium, SourceHanSansSC;
            font-weight: 500;
            color: #999999;
            line-height: 1.3125rem;
            letter-spacing: 0.0625rem;
        }

        .search_history {
            margin: 1.0625rem 0;
            width: 7.5rem;
            height: 0.875rem;
            font-size: 0.875rem;
            font-family: SourceHanSansSC-Medium, SourceHanSansSC;
            font-weight: 500;
            color: #FFFFFF;
            line-height: 1.3125rem;
            letter-spacing: 0.0625rem;
        }

        .line {
            width: 100%;
            height: 0.0625rem;
            background-color: RGB(48, 45, 60);
            margin-bottom: 1.0625rem;
        }

        .popular {
            font-size: 0.875rem;
            font-family: SourceHanSansSC-Medium, SourceHanSansSC;
            font-weight: 500;
            color: #999999;
            line-height: 1.3125rem;
            letter-spacing: 0.0625rem;
        }

        .topiclist {
            margin-top: 1.1875rem;

            .topic {
                // background-color: #FFFFFF;
                display: flex;
                margin-top: 1.8125rem;

                img:nth-child(1) {
                    margin-top: 0.3125rem;
                }

                view:nth-child(2) {
                    margin-left: 1.25rem;
                }

                view:nth-child(3) {
                    display: flex;
                    margin-left: 3.125rem;
                }
            }
        }
    }
</style>
