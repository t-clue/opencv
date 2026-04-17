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

# python build_xcframework.py --out <build dir>: <build dir>にビルドしたframeworkなどを作成する。<build dir>は自動で作成される
# --<platform>_archs <arch> : 指定したプラットフォーム, アーキテクチャのみ含める
# --build_only_specified_archs : 未指定のプラットフォームを含めない
# --without <module> : 指定したモジュールを含めずにビルドを行う
# note: 近年の macOS には `python` (Python 2) が同梱されていないため `python3` を使う。
# note: `--iphoneos_deployment_target` は Apps-iOS 側の `IPHONEOS_DEPLOYMENT_TARGET = 16.0` に合わせる。
#       14.0 / 15.0 を指定すると Xcode 26 系の iPhoneOS SDK ヘッダと整合せず `_stdio.h` 付近でビルドが失敗する。
python3 opencv/platforms/apple/build_xcframework.py --out ./build_xcframework --iphoneos_archs "arm64" --iphonesimulator_archs "x86_64,arm64" --build_only_specified_archs --without videoio --without video --without ts  --without python --without objdetect --without js --without java --without gapi --without dnn --without photo --iphoneos_deployment_target 16.0
```

zipコマンドで圧縮し、releaseページにアップロードしてください。
```
cd build_xcframework
zip -y -r opencv-4.8.0-ios-framework.zip opencv2.xcframework 
```
