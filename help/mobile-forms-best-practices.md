---
title: 行動表單最佳實務
description: 針對行動與離線表單使用案例，請透過Headless最適化Forms API建置您自己的原生應用程式並擷取表單定義。 原生行動應用程式的建議方法。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: 行動表單，原生應用程式，離線表單， headless API
index: true
exl-id: 6f25039f-61fc-4366-9e17-6b2809162c58
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# 行動表單最佳實務 {#mobile-forms-best-practices}

針對行動與離線表單使用案例，建議透過Headless最適化Forms API建立您自己的原生應用程式並擷取表單定義。 這可讓您完全掌控行動體驗，並確保隨著行動平台的發展而提供持續支援。

## 建議做法 {#recommended-approach}

建立符合以下條件的原生行動應用程式（iOS或Android）：

1. **擷取Headless表單定義** — 使用[Headless最適化Forms API](https://opensource.adobe.com/aem-forms-af-runtime/api/)來隨選擷取表單JSON （例如，當使用者在您的應用程式中開啟表單或導覽至該表單時）。 您可以列出可用表單，然後依ID擷取表單定義。

2. **在您的應用程式中轉譯表單** — 使用您偏好的UI架構（例如React Native或原生檢視）從JSON轉譯表單。 您可以在適合棧疊的位置使用Forms Web SDK和現有Headless調適型表單React元件，或建置您自己的使用相同JSON結構的轉譯器。

3. **可選擇支援離線** — 在您的應用程式中實作本機儲存並同步。 例如，線上上時快取表單定義、在本機儲存草稿，以及當裝置重新線上上時提交或同步資料。

這種方法可讓您的應用程式在Android和iOS變更時維持可維護性，並使用支援的Headless最適化Forms平台進行表單編寫、驗證和提交。

## 快速入門 {#getting-started}

* [AEM Headless最適化表單概觀](overview.md) — 功能和概念。
* [Headless適用性表單API](https://opensource.adobe.com/aem-forms-af-runtime/api/) — 以程式設計方式列出、擷取、驗證及提交表單。
* [架構](architecture.md) - Headless最適化表單如何運作，以及前端應用程式如何使用它們。

如需逐步整合，請參閱[建立並發佈Headless表單](create-and-publish-a-headless-form.md)和[開發人員入口網站](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=zh-Hant)。
