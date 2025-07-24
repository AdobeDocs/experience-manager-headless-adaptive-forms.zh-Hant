---
title: AEM Headless最適化Forms概述
description: AEM Headless最適化表單概觀。
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 4%

---


# 發行說明

歡迎使用Experience Manager Headless最適化表單率先採用者版本。 請閱讀下文，瞭解開始使用並充分利用此版本的資源和指示。

使用Adobe Experience Manager Headless調適型表單來建立具有前端架構(例如React、Angular等)的表單應用程式。 使用最適化Forms Web SDK進行狀態管理、驗證，並與其他接觸點整合。


早期採用者版本可讓您在[本機開發環境](setup-development-environment.md)中使用Headless最適化表單。 您可以使用本機開發環境來建置和測試Headless調適型表單。

Headless調適型表單會持續改善。 如欲瞭解最新發展，請定期造訪此頁面。 此頁面提供下列資訊：

* 搶先使用
* 最新版本
* 新功能
* 改善
* 錯誤修正
* 已棄用的功能
* 特殊指示
* 未來變更計劃

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## 早期採用者版本中可用的成品

在將Adobe Experience Manager Headless調適型表單帶給您的歷程中，以下成品可在早期採用者版本中使用：

### AEM Forms as a Cloud Service SDK

AEM Forms as a Cloud Service SDK可協助您建立、儲存及擷取Headless最適化表單。 它還有助於為Headless最適化表單提供預填、伺服器端規則驗證和提交服務。

### Forms Web SDK

Forms Web SDK提供API來驗證套用至表單各個欄位的限制，並勾選以將表單的JSON結構連線至UI架構。 此外，它還為Headless調適型表單提供React&#x200B;轉譯器，以協助將Headless調適型表單整合到您的應用程式。 下列是Web SDK的可用元件：

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)提供Headless最適化表單不同元件的概觀。 它還提供所有支援的元件、其對應屬性和限制的清單。

### Forms核心元件

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

核心元件是一組標準化的網頁內容管理(WCM)元件，可協助您加快開發時間並降低表單的維護成本。 Forms容器元件是核心元件。 它可協助您在Forms as a Cloud Service SDK的最適化Forms編輯器中內嵌及轉譯Headless最適化表單的JSON結構。

### 最適化Forms V2規格

Headless調適型表單規格提供定義Headless調適型表單可用的所有元件、限制和方法的詳細資訊。 此規格以[PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf)格式提供。

### HTTP和JS API

[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)可讓您列出、擷取、驗證、提交及追蹤Headless表單的提交狀態。<!-- URL is 404! [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) helps you use Headless adaptive forms with any JavaScript based UI framework. -->

### Visual Studio程式碼擴充功能

[Visual Studio Code擴充功能](visual-studio-code-extension-for-headless-adaptive-forms.md)可協助建立有效的JSON結構。 它為表單的JSON結構以及新增、刪除或重新命名JSON結構元件等常見功能提供IntelliSense支援和驗證。

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->