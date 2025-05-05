---
title: Headless最適化表單架構
description: 瞭解AEM Forms Headless最適化Forms的架構，以及它如何協助您快速建立各種平台的表單。 本文提供Headless Adaptive Forms如何運作，以及如何將其與不同應用程式整合以簡化表單建立程式的深入分析。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless，最適化表單，架構
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: c46ac28e490a09d6f563c4b5673d30a53c277a69
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---


# Headless最適化表單如何運作？

Headless最適化表單基本上是JSON結構（結構描述），由表單欄位（文字方塊、選擇和其他許多欄位）和對應的規則（條件邏輯）組成，以將互動行為新增到表單。 您可以在應用程式或網站中使用REST API來請求代管的JSON結構，並在應用程式或網站中將JSON結構以原生方式呈現為表單。 單一Headless最適化表單可提供多個網頁和應用程式，無需對其進行任何應用程式或網站特有的變更。

![Headless最適化表單的運作方式](/help/assets/how-headless-adaprive-forms-work.png)

## 架構 {#architecture}

典型的Headless最適化表單架構會構成Adobe Experience Manager Forms伺服器、在Adobe Experience Manager Forms伺服器上託管的Headless最適化表單，以及您用於頻道特定表單轉譯的前端應用程式(網站、行動應用程式、JavaScript應用程式、聊天應用程式等)。

Headless調適型表單部署的典型架構如下所示：

![架構](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Headless調適型表單實作的元件

**Adobe Experience Manager Server**：除了擔任Headless最適化表單的主機之外，Adobe Experience Manager還提供下列後端功能：

* RESTful APIs可列出、擷取、預填、驗證、提交、追蹤Headless表單的提交狀態。
* 視覺化編輯器，可輕鬆開發Headless最適化表單。
* Forms資料模型，用於接收資料或將資料傳送至不同的資料來源。
* 自動化複雜工作的工作流程引擎。

**Headless最適化表單**： Headless最適化表單會以.json檔案表示。 JSON結構會定義表單的元件、限制和結構。

**前端應用程式**：前端應用程式，例如SPA （單頁應用程式）、行動應用程式、JavaScript應用程式，使用Headless最適化表單（JSON表單表示）並在使用者端上轉譯表單。 您可以使用Headless調適型表單隨附的React轉譯器元件來轉譯調適型表單，或建置您自己的自訂元件以原生轉譯Headless調適型表單。

<!-- ### Understanding Headless adaptive forms definition -->



### 開發人員工具

在典型的開發週期中，您會先在Adobe Experience Manager Forms伺服器上建立和託管Headless調適型表單。 在第二個步驟中，您需要對應UI元件或使用公用UI元件庫(例如Google素材UI或Chakra UI)來設定表單的樣式。 在最後一個步驟中，您會擷取無頭式最適化表單並將其顯示在應用程式中(網站、行動應用程式、JavaScript應用程式、聊天應用程式或許多其他表面)。

下列工具可協助您建立Headless最適化表單，並將其整合至您的應用程式：

**Forms Web SDK （使用者端執行階段）**： Forms Web SDK是使用者端JavaScript資料庫。 它可讓您在表單欄位上套用使用者端驗證、維護表單的狀態，並提供勾點以將表單與UI層或調適型表單轉譯元件連線。 它可讓客戶驗證套用至表單各個欄位的限制，並勾選以將表單的JSON結構連線至UI架構。 Forms Web SDK包含下列元件：

* **商業規則處理器**：商業規則處理器接受表單JSON結構作為輸入、管理表單欄位的狀態、執行規則，以及JSON中存在的事件處理常式。
* **React繫結器**：提供掛接在控制器上，以將狀態新增至表單元件。 在預先填寫表單時也會很有幫助。
* **元件庫**：它會提供React Spectrum元件，並在React Binder模組中使用鉤點，將狀態新增至這些元件。

除了提供API來驗證套用至表單各個欄位的限制以外，Forms Web SDK還提供鉤點，以將Headless適用性表單連線至UI架構。 此外，它還為Headless調適型表單提供React&#x200B;轉譯器，以協助將Headless調適型表單整合到您的應用程式。 下列是Web SDK的可用元件：

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

所有這些元件都包含在AEM原型中。 當您為Headless調適型表單建立AEM Archetype 37或更新版本的專案時，專案中包含上述程式庫的最新版本。

* **程式碼遊樂場**： [程式碼遊樂場](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=zh-Hant)是專為開發人員設計的互動式環境，可試驗、瞭解及測試Headless最適化Forms的功能。

**已啟動的應用程式**：Adobe也已發行已啟動的應用程式，以協助您快速啟動Headless最適化表單。

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**： [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)提供Headless最適化表單不同元件的概觀。 它還提供所有支援的元件、其對應屬性和限制的清單。

**Visual Studio程式碼擴充功能**： [Visual Studio程式碼擴充功能](visual-studio-code-extension-for-headless-adaptive-forms.md)可協助建立有效的JSON結構。 它為表單的JSON結構以及新增、刪除或重新命名JSON結構元件等常見功能提供IntelliSense支援和驗證。

**HTTP與JavaScript API**： [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)可讓您列出、擷取、驗證、提交、追蹤Headless表單的提交狀態。 [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/)可協助您將無頭式最適化表單與任何JavaScript式UI架構搭配使用。

**JSON公式**：這是Forms運算式文法的實作，可協助您查詢JSON結構並建立Headless適用性表單的規則。 文法是試算表型函式和運運算元的組合，以及[JMESPath](https://jmespath.org/) JSON查詢語言。 您可以使用[遊樂場](https://opensource.adobe.com/json-formula/dist/index.html)來探索JSON公式語法和功能。

**最適化Forms 2.0版規格**：最適化Forms 2.0版規格提供定義Headless最適化表單可用的所有元件、限制和方法的詳細資訊。 規格以[PDF](/help/assets/headless-adaptive-forms-specification.pdf)格式提供。

