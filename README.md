## OpenCV: Open Source Computer Vision Library

- [本家リポジトリ](https://github.com/opencv/opencv)

本リポジトリは、最新のxcodeでビルドしたopencv2.frameworkをreleaseページにアップロードするために作成されたリポジトリです。
DR内ではreleaseページにアップロードされたopencv2.frameworkをCarthageでインストールし、利用することになります。

### ビルド環境


### swift opencv2.frameworkのビルド
ビルドは、本家のリポジトリを使用して行います。
```
cd ~/
git clone https://github.com/opencv/opencv
```

使用したいバージョンに移動
```
cd opencv
git checkout 4.6.0
```

ビルド
作成されたiosディレクトリ内にopencv2.frameworkが作成されます。
```
cd ~/
python3 opencv/platforms/ios/build_framework.py --without videoio --without video --without ts  --without python --without objdetect --without js --without java --without gapi --without dnn --without photo ios
```

zipコマンドで圧縮し、releaseページにアップロードしてください。
```
cd ios
zip -r opencv-4.6.0-ios-framework.zip opencv2.framework 
```
