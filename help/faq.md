---
title: 關於Headless最適化Forms的常見問題
description: 常見問題
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless，最適化表單，常見問題
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---

# 常見問題集 (FAQ) {#headless-adaptive-forms-faq}

## 如要使用Headless調適型表單，我應該知道React.js嗎？

您可以使用任何架構、資料庫或語言來轉譯Headless調適型表單，並使用Adobe的REST API來驗證及提交表單。 現成提供的AF核心程式庫與架構無關。 React-Render和React-component程式庫也隨附現成可用的功能，方便您使用。 您可以建置自己的元件；不限於提供的元件。


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## 是否需要Forms as a Cloud Service沙箱才能使用Headless最適化表單？

您可以使用入門應用程式來開始開發和設定Headless最適化表單的樣式。 您需要Forms as a Cloud Service來託管及提供Headless最適化表單與後端表單功能。

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## 哪裡可以取得Headless最適化表單的預覽？ {#storybook-example}

您可以使用入門應用程式來轉譯及預覽自訂Headless最適化表單。 您也可以修改[故事簿](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction)範例以預覽Headless最適化表單。

![](/help/assets/storybook-example.png)

## 是否可以將Headless調適型表單與自訂架構搭配使用？

Headless最適化表單是以[標準規格](/help/assets/headless-adaptive-forms-specification.pdf)為基礎。 您可以擴充規格以使用它來建置自訂元件。 例如，Chakra UI、Vue.js等元件。

## Headless調適型表單是否支援階層式欄位？

在階層式欄位中，第二個欄位的內容取決於在第一個欄位中選擇的內容。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType：drop-down；formJson.items[0].minimum：！undefined；formJson.items[0].maximum：！undefined；formJson.items[0].label.value：Choose+number+of+options；formJson.items[0].enum[0]：1；formJson.items[0].enum[1]：2；formJson.items[1].fieldType：drop)提供階層式欄位的範例。

## Headless最適化表單是否允許使用個人化資料預先填寫表單？

Headless最適化表單允許使用個人化資料預先填寫表單。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)提供如何預填Headless最適化表單的範例。

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## 我可以搭配Angular SPA使用Headless最適化表單嗎？

您可以使用Web SDK整合Headless最適化表單與Angular SPA。 它獨立於任何框架。 您可以使用React SDK作為參考。

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## 是否有任何外掛程式可讓Headless AF的開發更輕鬆？

是 — Visual Studio Code擴充功能可讓您在JSON中手動編寫Headless最適化表單。

## Headless最適化表單可以連線到任何CRM以讀取或寫入資料嗎？

您可以使用Microsoft Dynamics和Salesforce來提交或預填Headless最適化表單。 除了CRM，Headless最適化表單支援使用REST端點、電子郵件和自訂提交動作提交或預填。
