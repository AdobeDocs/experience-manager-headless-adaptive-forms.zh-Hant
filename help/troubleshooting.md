---
title: Headless最適化Forms疑難排解
description: Headless最適化Forms疑難排解
keywords: headless，最適化表單，疑難排解
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 5%

---

# 疑難排解

## 無法在本機開發環境中部署原型專案

### 問題

當您使用`mvn -PautoInstallPackage clean install`或類似的命令來部署AEM Archype專案時，該專案將無法部署。

### 原因

發生此情況可能是因為node.js或NPM的版本不受支援或安裝損毀。

### 解決方案

1. 從您的環境中完全[移除目前的Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/)安裝。

1. 使用NPM安裝Node.JS 16.13.0或更新版本。

1. 重新啟動您的電腦。


## `mvn clean install`命令無法執行

### 問題

當您使用`mvn clean install`或類似的命令來部署AEM Archype專案時，命令無法執行。

### 原因

如果未安裝Git，便會發生此狀況。

### 解決方案

下載並安裝[最新版的Git](https://git-scm.com/downloads)。 若您為Git的新手，請參閱[安裝Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。
