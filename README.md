WeChatQrCode添加单独返回二维码的位置信息函数

opencv wechat_qrcode模块只支持识别qrcode, 不能识别datamatrix类型的二维码

修改了WeChatQrcode代码，添加了对外的公共函数detectNew，可以返回二维码的位

置信息，然后可以采用其它的识别库识别datamatrix类型的二维码。

代码版本来自4.8.1


```C++
vector<Mat> WeChatQRCode::detectNew(InputArray img) {
    CV_Assert(!img.empty());
    CV_CheckDepthEQ(img.depth(), CV_8U, "");

    auto points = vector<Mat>();

    if (img.cols() <= 20 || img.rows() <= 20) {
        return points;
    }
    Mat input_img;
    int incn = img.channels();
    CV_Check(incn, incn == 1 || incn == 3 || incn == 4, "");
    if (incn == 3 || incn == 4) {
        cvtColor(img, input_img, COLOR_BGR2GRAY);
    } else {
        input_img = img.getMat();
    }
    return p->detect(input_img);
}
