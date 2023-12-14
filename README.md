## OpenCV: Open Source Computer Vision Library

- [本家リポジトリ](https://github.com/opencv/opencv)

本リポジトリは、最新のxcodeでビルドしたopencv2.frameworkをreleaseページにアップロードするために作成されたリポジトリです。

### swift opencv2.frameworkのビルド
```
cd ~/
git clone git@github.com:t-clue/opencv.git
```

本家のリポジトリから使用したいバージョンをチェックアウト
```
cd opencv
git remote add upstream https://github.com/opencv/opencv
git fetch upstream
git checkout 4.8.0
```

ビルド
作成されたiosディレクトリ内にopencv2.frameworkが作成されます。
```
cd ~/
# 必要ならばcmakeをインストール
brew install cmake

# python3 build_xcframework.py --out <build dir>: <build dir>にビルドしたframeworkなどを作成する。<build dir>は自動で作成される
# --without <module> : 指定したモジュールを含めずにビルドを行う
python3 opencv/platforms/apple/build_xcframework.py --without videoio --without video --without ts  --without python --without objdetect --without js --without java --without gapi --without dnn --without photo --out ./build_xcframework
```

zipコマンドで圧縮し、releaseページにアップロードしてください。
```
cd ios
zip -r opencv-4.6.0-ios-framework.zip opencv2.framework 
```
