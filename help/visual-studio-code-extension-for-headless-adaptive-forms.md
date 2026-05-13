---
title: Headless最適化表單的Visual Studio Code擴充功能
description: Headless最適化表單的Visual Studio Code擴充功能
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: Headless，適用性表單，Visual Studio程式碼擴充功能
index: true
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
TQID: https://experienceleague.adobe.com/sf8qkVgbwMf2CGDsATHRYzq6idFQNFv3Os89oiCoiLU
product_v2: id: e8f6de9b-cf88-4405-8d10-15efa08c230eid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 231
ht-degree: 0%

---

# 適用於Headless最適化表單的Microsoft Visual Studio Code擴充功能

如果您使用® Visual Studio Code做為IDE （整合式開發環境），您可以使用適用於Microsoft Visual Studio Code的Adaptive Forms擴充功能。 擴充功能：

* 在Visual Studio Code中新增最適化Forms的IntelliSense功能。
* 協助驗證及自動完成Headless最適化表單元件的JSON語法。
* 輕鬆地在面板中導覽Headless最適化表單的結構。
* 協助翻譯Headless最適化表單。

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## 先決條件

* 下載並安裝[Microsoft Visual Studio Code 1.62.0或更新版本](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version)。 如果您已安裝舊版或未安裝版本，請從[Microsoft網站](https://code.visualstudio.com/docs/setup/setup-overview)下載最新版本。 若要從Apple macOS上的命令列使用Visual Studio，請參閱[從命令列啟動](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)。
* 下載[最適化表單產生器擴充功能](/help/assets/adaptive-form-builder-0.12.0.vsix)。

## 安裝擴充功能

1. 開啟命令提示字元並瀏覽至包含已下載擴充功能檔案&#x200B;*adaptive-form-builder-[version].vsix*&#x200B;的目錄。

1. 執行以下命令來安裝擴充功能：

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![正在安裝擴充功能](/help/assets/install-extension.png)


   如需.vsix檔案的相關資訊，請參閱[Microsoft Visual Studio Code說明](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_install-from-a-vsix)。
