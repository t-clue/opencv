## OpenCV: Open Source Computer Vision Library

- [本家リポジトリ](https://github.com/opencv/opencv)

本リポジトリは、最新のxcodeでビルドしたopencv2.frameworkをreleaseページにアップロードするために作成されたリポジトリです。
DR内ではreleaseページにアップロードされたopencv2.frameworkをCarthageでインストールし、利用することになります。

### ビルド環境
- xcode
- python3
- cmake
- swift

### swift opencv2.frameworkのビルド
```
cd ~/
git clone git@github.com:t-clue/opencv.git
```

使用したいバージョンに移動
```
cd opencv
git remote add upstream https://github.com/opencv/opencv
git fetch upstream
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
