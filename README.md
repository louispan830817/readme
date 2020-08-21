# 熱更新流程說明

## 目錄
- [目標](#目標)
- [用途說明](#用途說明)
- [環境](#環境)
- [熱更新流程](#熱更新流程)


## 目標

- 經由熱更新做到即時更新功能

## 用途說明

- 版本號需與當前APP上架版本相符下對應指令達到熱更新

## 環境

目前在Microsoft App Center有分成三個：Production / Dev

![](https://i.imgur.com/JVGXxDW.png)

- CodePushKey:

    - WistronAppCodePush_Android
      - Production:EbE37ZOFNN_OZuwQ2Xr4HOUaMPhdaHBRwY6tK
      - Dev:nBJPP3Im4GeBWOsOGVqA2QTY2OrV8FBCzUTO0
    - WistronAppCodePush_IOS  
      - Production:zb_GcHajJXB0UXPHxAQn3dNeisxeu3VbUoF9F
      - Dev:6mVWPGudFRWmDSE1YZQ-wt-0a9ccfTyLWUEpm
    - WixtraAppCodePush_Android
      - Production:9lXMUuayMMnLPHt3OwA1MwPFQYbhdlhFRJNKd
      - Dev:m364zLqLx56LAGlke51eRNqiQZnIiAkg0I3Wh
    - WixtraAppCodePush_IOS
      - Production:RadXnF2lfP64yMhQwitlYDteO7O7aZv7dDACW
      - Dev:yck0-AUUXvh4wTFNTWI0LPGMGq26jnx4V2eU9

## 熱更新流程

- 流程圖

![](https://i.imgur.com/RYU8xTl.png)

- 熱更新更版流程
  - APPCenter 進行登入 
    - appcenter login

  - 熱更新更版指令(注意更版請確認功能是否確認完善再進行更版<總共4版>)
    - code-push release-react(指令) + 團隊名稱/APPCENTER專案名稱 ＋ device --d + 環境(Production/Dev) --t + 版本號 --m + 強制更新(true/false)
      - code-push release-react wieduapp/WistronAppCodePush_IOS ios --d Production --t 2.0.3 --m true
      - code-push release-react wieduapp/WistronAppCodePush_Android android --d Production --t 2.0.3 --m true
      - code-push release-react wieduapp/WixtraAppCodePush_IOS ios --d Production --t 2.0.3 --m true
      - code-push release-react wieduapp/WixtraAppCodePush_Android android --d Production --t 2.0.3 --m true