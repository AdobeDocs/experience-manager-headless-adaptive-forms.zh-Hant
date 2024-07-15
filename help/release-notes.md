---
title: AEM Headless最適化表單概述
description: AEM Headless最適化表單概觀。
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 3%

---


# 發行說明

歡迎使用Experience ManagerHeadless最適化表單早期採用者版本。 請閱讀下文，瞭解開始使用並充分利用此版本的資源和指示。

您可以使用Adobe Experience Manager Headless調適型表單來建立使用前端UI架構(如React、Angular等)的表單應用程式，並使用Adaptive Forms Web SDK進行狀態管理、驗證及與各種其他接觸點整合等功能。

早期採用者版本可讓您在[本機開發環境](setup-development-environment.md)中使用Headless最適化表單。 您可以使用本機開發環境來建置和測試Headless調適型表單。

Headless調適型表單會持續進行改善。 如欲瞭解最新發展，請定期造訪此頁面。 本頁提供搶先使用、最新版本、新功能、改善功能、錯誤修正、過時功能、特殊指示和未來變更計畫的相關資訊。

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

### AEM FORMSAS A CLOUD SERVICESDK

AEM Formsas a Cloud ServiceSDK可協助您建立、儲存及擷取Headless最適化表單。 它還有助於為Headless最適化表單提供預填、伺服器端規則驗證和提交服務。

### Forms Web SDK

Forms Web SDK提供API來驗證套用至表單各個欄位的限制，並勾選以將表單的JSON結構連線至UI架構。 此外，它還為Headless調適型表單提供React&#x200B;轉譯器，以協助將Headless調適型表單整合到您的應用程式。 下列Web SDK元件可供使用：

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)提供Headless最適化表單不同元件的概觀。 它還提供所有支援的元件、其對應屬性和限制的清單。

### Forms核心元件

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

核心元件是一組標準化的網頁內容管理(WCM)元件，可協助您加快開發時間並降低表單的維護成本。 Forms容器元件是核心元件。 它可協助您在Forms as a Cloud Service SDK的調適型Forms編輯器中內嵌及轉譯Headless調適型表單的JSON結構。

### 最適化Forms V2規格

Headless調適型表單規格提供定義Headless調適型表單可用的所有元件、限制和方法的詳細資訊。 規格以[PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf)格式提供。

### HTTP和JS API

[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)可讓您列出、擷取、驗證、提交、追蹤Headless表單的提交狀態。 [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/)可協助您將無頭式最適化表單與任何JavaScript式UI架構搭配使用。

### Visual Studio程式碼擴充功能

[Visual Studio Code擴充功能](visual-studio-code-extension-for-headless-adaptive-forms.md)可協助建立有效的JSON結構。 它提供表單的JSON結構的IntelliSense支援和驗證，以及一般功能，例如JSON結構的新增、刪除或重新命名元件。

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->