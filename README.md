## opencv_contrib

opencv wechat_qrcode模块只支持识别qrcode, 不能识别datamatrix类型的二维码

修改了WeChatQrcode代码，添加了对外的公共函数detectNew，可以返回二维码的位置

信息，然后可以采用其它的识别库识别datamatrix类型的二维码。
