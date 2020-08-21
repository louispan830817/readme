# WistronHrApp - X2B交接

## 目錄

- [環境的修改(補充，ios詳細請看交接文件)](#環境的修改補充ios詳細請看交接文件)
- [套件的修改](#套件的修改)
- [建立開發環境](#建立開發環境)
- [Native code修改](#native-code修改)
- [Known issue](#known-issue)



## 環境的修改(補充，ios詳細請看交接文件)

- IOS
  - test case這邊的Team也要修改成自己專案的ID
    - ![image-202005141155287891](./x2b Hand-Over/img/image-202005141155287891.png)
  - 這種錯誤訊息 `Model is running iOS 10.2 (14C92), which may not be supported by this version of Xcode`
    - 解法為至 [iGhibli/iOS-DeviceSupport ](<https://github.com/iGhibli/iOS-DeviceSupport/tree/master/DeviceSupport>) 下載相對應沒有的zip檔，以這個錯誤為例，就要下載 [**10.2 (14C92).zip**](https://github.com/iGhibli/iOS-DeviceSupport/blob/master/DeviceSupport/10.2%20(14C92).zip) ，於本機端解壓縮後，將資料夾放在 `~/Library/Developer/Xcode/iOS DeviceSupport/` 中
      - 下圖為示例
      - ![image-20200518154009353](./x2b Hand-Over/img/image-20200518154009353.png)
    - 也可以參考 [Xcode Releases](<https://xcodereleases.com/>)

- Android
  - 修改記錄在 git commit `b5b7b8199331c7100af18ee3e4807bf628024112`
  - 遇到兩個問題
    - 一個是react-native run-android後，發生`:app:transformClassesWithMultidexlistForDebug FAILED`
      - 最主要的解法是升級 **minSdkVersion至21(Android 5.0)** 就好了!
    - 另一個是打開Android Studio後，發現`[@react-native-community_async-storage, react-native-community_async-storage] point to the same directory in the file system. Each module must have a unique path.`
      - 最主要的解法是使用`react-native unlink @react-native-community_async-storage`，就可以了





## 套件的修改

- 詳見交接文件！
- react-native-orientation 的 Android src code
- react-native-video 的 Android src code



## 建立開發環境

- 流程 (適用於RN 0.60後)
  - 拿到src code (從git上將code下載下來)
  - 執行`yarn install`或是`npm install`來安裝套件
  - 執行指令 `pod install`，將ios的套件與ios連動
  - 根據[環境的修改(補充，ios詳細請看交接文件)](#環境的修改補充ios詳細請看交接文件)和[套件的修改](#套件的修改)來修改環境
  - 執行`react-native run-android` 來跑Android的開發環境 和 `react-native run-ios` 來跑IOS的開發環境





## Native code修改

- 詳見交接文件！
- 讓Android code使用的方法數增加上限
  - Android的function數上限是65536，所以multiDexEnabled設成true避免這個上限
  - 於 `../android/app/build.gradle` 修改
  - ![image-20200518155524612](./x2b Hand-Over/img/image-20200518155524612.png)
- 偵測錄影
  - IOS
    - ios/ScreenRecorder.h
    - ios/ScreenRecorder.m
  - Android
    - android\app\src\main\java\com\wiedu_x2b_app\MainActivity.java
- 檢查Android app是否可以打開這個類型的app
  - android\app\src\main\java\com\wiedu_x2b_app\
    - RNTriggerIntent.java
    - RNTriggerIntentPackage.java
    - MainApplication.java



## Known issue

- 使用Xcode 11 build的話，無法在iOS 13的手機偵測錄影，交接時是用Xcode 10.3 build的！





