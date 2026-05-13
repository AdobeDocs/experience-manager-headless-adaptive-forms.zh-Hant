---
title: 關於Headless最適化Forms的常見問題
description: 常見問題
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless，最適化表單，常見問題
index: true
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
TQID: https://experienceleague.adobe.com/GqYwqgwHe82HXLvljMyGW4PDOkmi7Xg2MKjYxibsFnY
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: f013e6ab-27b8-4645-b5a7-31ffa474d04f
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 837
ht-degree: 0%

---

# 常見問題 (FAQ) {#headless-adaptive-forms-faq}

## 如要使用Headless調適型表單，我應該知道React.js嗎？

您可以使用任何架構、資料庫或語言來轉譯Headless調適型表單，並使用Adobe的REST API來驗證及提交表單。 現成提供的AF核心程式庫與架構無關。 React-Render和React-component程式庫也隨附現成可用的功能，方便您使用。 您可以建置自己的元件；不限於提供的元件。


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## 是否需要Forms as a Cloud Service沙箱才能使用Headless最適化表單？

您可以使用入門應用程式來開始開發和設定Headless最適化表單的樣式。 您需要Forms as a Cloud Service來託管及提供Headless最適化表單與後端表單功能。

<!-- 
## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. 
-->

## 哪裡可以取得Headless最適化表單的預覽？ {#storybook-example}

您可以使用入門應用程式來轉譯及預覽自訂Headless最適化表單。 您也可以修改[故事簿](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction)範例以預覽Headless最適化表單。

![](/help/assets/storybook-example.png)

## 是否可以將Headless調適型表單與自訂架構搭配使用？

Headless最適化表單是以[標準規格](/help/assets/headless-adaptive-forms-specification.pdf)為基礎。 您可以擴充規格以使用它來建置自訂元件。 例如，Chakra UI、Vue.js等元件。

## Headless調適型表單是否支援階層式欄位？

在階層式欄位中，第二個欄位的內容取決於在第一個欄位中選擇的內容。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType：drop-down；formJson.items[0].minimum：！undefined；formJson.items[0].maximum：！undefined；formJson.items[0].label.value：Choose+number+of+options；formJson.items[0].enum[0]：1；formJson.items[0].enum[1]：2；formJson.items[1].fieldType：drop)提供階層式欄位的範例。

## Headless最適化表單是否允許使用個人化資料預先填寫表單？

Headless最適化表單允許使用個人化資料預先填寫表單。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)提供如何預填Headless最適化表單的範例。

<!--
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  
-->

## 我可以搭配Angular SPA使用Headless最適化表單嗎？

您可以使用Web SDK整合Headless最適化表單與Angular SPA。 它獨立於任何框架。 您可以使用React SDK作為參考。

<!--
## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 
-->

## 是否有任何外掛程式可讓Headless AF的開發更輕鬆？

是 — Visual Studio Code擴充功能可讓您在JSON中手動編寫Headless最適化表單。

## 行動或離線表單的建議作法為何？ {#mobile-offline-forms}

透過Headless最適化Forms API建置您自己的原生應用程式並擷取表單定義。 您可以選擇實作離線支援（例如，本機儲存和同步）。 請參閱[行動表單最佳實務](mobile-forms-best-practices.md)，以取得建議的方法和API連結。

## 如何搭配AEM Forms使用GraphQL或Headless API？

AEM Headless最適化Forms使用&#x200B;**HTTP/REST API**，而非GraphQL。 應用程式會呼叫這些API來列出表單、擷取表單定義(JSON)、驗證、提交和追蹤提交狀態。 使用[Headless最適化表單HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)以取得完整參考。 如需如何擷取及轉譯表單，請參閱[架構](architecture.md)和[瞭解Headless表單](understanding-headless-forms.md)。

## 如何使用Adobe AEM Forms中的React元件來實作和設計Headless表單樣式？

您可以使用自己的React元件和CSS （或UI程式庫，例如素材UI）來實作和設定Headless表單的樣式。 表單邏輯（狀態、驗證和規則）來自Forms Web SDK和表單JSON；您的應用程式會提供轉譯它的UI。

* 若要使用React UI程式庫來設定Headless表單的樣式，請參閱[使用自訂react程式庫來呈現Headless表單](use-google-material-ui-react-components-to-render-a-headless-form.md)。
* 若要建置自訂React元件並將它們對應至表單欄位，請參閱[使用自訂元件來轉譯Headless表單](developing-for-headless-forms-using-your-own-components.md)。

如需何時使用Headless表單、狀態管理和驗證等概念，請參閱[瞭解Headless表單](understanding-headless-forms.md)。

## 如何使用自訂CSS、主題、規則編輯器和Headless表單來實作和自訂AEM Forms？

**Headless表單：**&#x200B;樣式與外觀完全由您控制。 您使用自己的React （或其他）元件和自己的CSS；沒有內建主題。 請參閱[使用自訂react程式庫來轉譯Headless表單](use-google-material-ui-react-components-to-render-a-headless-form.md)和[使用自訂元件來轉譯Headless表單](developing-for-headless-forms-using-your-own-components.md)來實作和設定Headless表單的樣式。

**傳統AEM Forms （主題、規則編輯器、視覺編輯器）：**&#x200B;自訂CSS、主題編輯器和規則編輯器套用至傳統（非headless）最適化Forms編寫體驗。 如需這些主題，請參閱Experience League上的[AEM Forms檔案](https://experienceleague.adobe.com/docs/experience-manager-forms.html)。

## Headless最適化表單可以連線到任何CRM以讀取或寫入資料嗎？

您可以使用Microsoft Dynamics和Salesforce來提交或預填Headless最適化表單。 除了CRM，Headless最適化表單支援使用REST端點、電子郵件和自訂提交動作提交或預填。
