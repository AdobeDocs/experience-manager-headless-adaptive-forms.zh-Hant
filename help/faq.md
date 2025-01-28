---
title: 常見問題
description: 常見問題
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless，最適化表單，常見問題
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: c46ac28e490a09d6f563c4b5673d30a53c277a69
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---

# 常見問題集(FAQ) {#headless-adaptive-forms-faq}

## 如要使用Headless調適型表單，我應該知道React.js嗎？

您可以使用任何架構、資料庫或語言來轉譯Headless調適型表單，並使用我們的REST API來驗證及提交表單。 AF核心程式庫（提供OOTB）獨立於架構。 提供OOTB的React-Render和React-component程式庫方便您使用。 您可以開發自己的元件，而不受限於使用這些元件。

<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## 是否需要Forms as a Cloud Service沙箱才能使用Headless最適化表單？

您可以使用入門應用程式來開始開發和設定Headless最適化表單的樣式。 您需要Formsas a Cloud Service來託管及提供Headless最適化表單與後端表單功能。

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## 我可以在哪裡預覽Headless最適化表單？ {#storybook-example}

您可以使用入門應用程式來轉譯及預覽自訂Headless最適化表單。 您也可以修改[故事簿](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction)範例以預覽Headless最適化表單。

![](/help/assets/storybook-example.png)

## 是否可以將Headless調適型表單與自訂架構搭配使用？

Headless最適化表單是以[標準規格](/help/assets/headless-adaptive-forms-specification.pdf)為基礎。 您可以擴充規格以使用它來建置自訂元件。 例如，Chakra UI、Vue.js等元件。

## Headless調適型表單是否支援階層式欄位？

在階層式欄位中，第二個欄位的內容取決於在第一個欄位中選擇的內容。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&amp;args=formJson.items[0].fieldType：drop-down；formJson.items[0].minimum：！undefined；formJson.items[0].maximum：！undefined；formJson.items[0].label.value：Choose+number+of+options；formJson.items[0].enum[0]：1；formJson.items[0].enum[1]：2；formJson.items[1].fieldType：drop)提供階層式欄位的範例。

## Headless最適化表單是否允許使用個人化資料預先填寫表單？

Headless最適化表單允許使用個人化資料預先填寫表單。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)提供如何預填Headless最適化表單的範例。

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## 我可以搭配AngularSPA使用Headless最適化表單嗎？

您可以使用網頁SDK整合Headless最適化表單與AngularSPA。 它獨立於任何框架。 您可以使用React SDK作為參考。

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## 是否有任何外掛程式可讓Headless AF的開發更輕鬆？

是，擴充功能可用於Microsoft Visual Studio Code。 它提供了一種手動編寫Headless最適化表單JSON的便利方法。

## Headless最適化表單可以連線到任何CRM以讀取或寫入資料嗎？

您可以使用Microsoft Dynamics和Salesforce來提交或預填Headless最適化表單。 除了CRM，Headless最適化表單支援使用REST端點、電子郵件和自訂提交動作提交或預填。
