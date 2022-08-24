<template>
    <!-- 提交举报 -->
    <view>
        <view class="head">
            <view @click="goBack" class="goBack">
                <image src="../../static/report/back01.png"></image>
            </view>
            <view class="head_title">举报</view>
        </view>
        <!-- <view class="line">

        </view> -->
        <view class="content">
            <u--form :rules="rules" :model="form" ref="uForm">
                <u-form-item>
                    <view class="content_title">
                        <view class="">
                            截图证据(必填)
                        </view>
                        <view class="content_title_right">
                            0/6
                        </view>
                    </view>
                </u-form-item>
                <!-- 上传 -->
                <u-form-item prop="photo">
                    <view class="upload">
                        <u-upload :fileList="fileList" @afterRead="afterRead" @delete="deletePic" name="1" multiple
                            :maxCount="10">

                            <image src="../../static/report/upload.png" mode="widthFix"
                                style="width: 109px;height: 109px;">
                            </image>
                        </u-upload>
                        <text class="upload_text">
                            添加图片
                        </text>
                    </view>
                </u-form-item>
                <view class="line_two">

                </view>
                <!-- 补充内容 -->
                <view class="replenish">
                    补充内容(选填)
                </view>
                <u-form-item>
                    <u--textarea v-model="value2" placeholder="记录这一刻，分享给懂你的Ta~"
                        placeholderStyle="color: #CFCFCF; font-size: 14px;" confirmType="done">
                    </u--textarea>
                </u-form-item>
            </u--form>
        </view>
        <view class="submit">
            <button class="button" @click="submit">
                提交
            </button>
        </view>
    </view>
</template>

<script>
    export default {
        data() {
            return {
                //上传
                fileList: [],
                // 文本域
                value2: '',
                // 校验图片
                form: {
                    photo: ''
                },
                rules: {
                    'photo': {
                        type: 'string',
                        required: true,
                        message: '请上传图片',
                        trigger: ['blur', 'change']
                    }

                }
            }

        },
        methods: {

            // 删除图片
            deletePic(event) {
                this[`fileList${event.name}`].splice(event.index, 1)
            },
            // 新增图片
            async afterRead(event) {
                // 当设置 mutiple 为 true 时, file 为数组格式，否则为对象格式
                let lists = [].concat(event.file)
                let fileListLen = this[`fileList${event.name}`].length
                lists.map((item) => {
                    this[`fileList${event.name}`].push({
                        ...item,
                        status: 'uploading',
                        message: '上传中'
                    })
                })
                for (let i = 0; i < lists.length; i++) {
                    const result = await this.uploadFilePromise(lists[i].url)
                    let item = this[`fileList${event.name}`][fileListLen]
                    this[`fileList${event.name}`].splice(fileListLen, 1, Object.assign(item, {
                        status: 'success',
                        message: '',
                        url: result
                    }))
                    fileListLen++
                }
            },
            uploadFilePromise(url) {
                return new Promise((resolve, reject) => {
                    let a = uni.uploadFile({
                        url: '', // 真实的接口地址
                        filePath: url,
                        name: 'file',
                        formData: {
                            user: 'test'
                        },
                        success: (res) => {
                            setTimeout(() => {
                                resolve(res.data.data)
                            }, 1000)
                        }
                    });
                })

            },

            // 提交
            submit() {
                this.$refs.uForm.validate().then(res => {
                    uni.$u.toast('校验通过')
                }).catch(errors => {
                    uni.$u.toast('校验失败')
                })
            }
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

    .line {
        border: 0.6px dashed #ccc;
        margin-top: 0.9375rem;
    }

    .content {
        margin: 0 1.25rem;

        /deep/ .content_title {
            width: 100%;
            margin: 1.0625rem 0;
            font-size: 0.875rem;
            font-family: SourceHanSansSC-Bold, SourceHanSansSC;
            font-weight: bold;
            color: #CFCFCF;
            line-height: 1.3125rem;
            display: flex;
            justify-content: space-between;

            /deep/ .content_title_right {
                width: 1.3125rem;
                height: 0.75rem;
                font-size: 0.75rem;
                font-family: SourceHanSansSC-Medium, SourceHanSansSC;
                font-weight: 500;
                color: #999999;
                line-height: 1.125rem;
            }
        }

        .upload {
            position: relative;
            width: 100%;
            height: 6.8125rem;

            // background-color: #FFFFFF;
            image {
                width: 6.8125rem;
                height: 6.8125rem;
            }

            .upload_text {
                position: absolute;
                margin-top: -1.875rem;
                margin-left: 1.85rem;
                color: #FFFFFF;
            }
        }

        .line_two {
            border: 0.6px dashed #ccc;
            margin-top: 1.75rem;
        }

        .replenish {
            margin-top: 1.5625rem;
            font-size: 0.875rem;
            font-family: SourceHanSansSC-Bold, SourceHanSansSC;
            font-weight: bold;
            color: #FFFFFF;
            line-height: 1.3125rem;
            margin-bottom: 1.0625rem;
        }

        /deep/.u-textarea {
            border-radius: 0.25rem;
            background-color: RGB(54, 50, 70);
            position: relative;
            display: flex;
            flex-direction: row;
            border: none;
            flex: 1;
            padding: 0.5625rem;
        }
    }

    .button {
        margin: 0 auto;
        width: 20.25rem;
        height: 2.625rem;
        position: fixed;
        bottom: 1.25rem;
        left: 1.5625rem;
        font-size: 0.9375rem;
        font-family: SourceHanSansSC-Bold, SourceHanSansSC;
        font-weight: bold;
        color: #63361E;
        line-height: 2.625rem;
        background-color: RGB(251, 222, 189);
    }
</style>
