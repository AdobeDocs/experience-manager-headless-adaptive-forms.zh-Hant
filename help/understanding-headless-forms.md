---
title: 瞭解Headless表單 — 概念與常見問答
description: 回答有關Headless表單是什麼、與傳統表單程式庫有何不同、實作詳細資料、UI控制、效能以及與架構和後端整合的常見問題。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: Headless forms， headless form library，無頭表單庫， adaptive forms，最適化表單，狀態管理，驗證， design system，設計系統， SSR， CMS
index: true
exl-id: 539da3e9-25c5-4e26-ba4e-f68cf849bca4
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 0%

---

# 瞭解Headless表單 — 概念與常見問答 {#understanding-headless-forms}

本指南會回答有關Headless表單的一般常見問題，以及如何將其套用至AEM Headless最適化Forms。 用它來決定何時使用Headless方法，以及如何在棧疊中實作、樣式化和整合表單。

## 基本概念與瞭解 {#basics-understanding}

### 什麼是Headless表單程式庫？

**Headless表單程式庫**&#x200B;是將&#x200B;**表單邏輯** （狀態、驗證、規則、提交）與&#x200B;**簡報** （UI元件和樣式）分開的表單解決方案。 「head」是可見的表單UI；「headless」表示資料庫不會指定或傳送固定UI。 相反地，它會公開：

* **表單模型** （通常是JSON）：結構、欄位、限制和規則。
* **API或鉤點**&#x200B;可讀取和更新表單狀態、執行驗證及處理提交。
* **事件和生命週期**，讓您的UI能夠回應變更。

在AEM Headless最適化Forms中，表單是託管在Adobe Experience Manager上的[JSON結構](architecture.md)。 [Forms Web SDK](architecture.md#developer-tools) （使用者端執行階段）提供邏輯層（商業規則處理器、狀態管理、驗證），而您的應用程式則提供呈現該結構的UI。

### Headless表單與傳統表單庫有何不同？

| 層面 | 傳統表單庫 | Headless表單資料庫 |
|--------|---------------------------|------------------------|
| **UI** | 隨附內建元件和樣式 | 沒有規定的UI；您自備元件 |
| **樣式** | 程式庫元件的主題設定或覆寫 | 完全控制；依原樣使用您的設計系統 |
| **表單定義** | 通常僅限程式碼（JSX/HTML中的元件） | 通常資料導向（來自CMS或API的JSON/結構描述） |
| **狀態與驗證** | 繫結至程式庫元件 | 透過API/鉤子公開；任何UI都可以繫結到它們 |
| **管道** | 通常為網頁（有時為一個框架） | 相同的表單定義可以驅動網頁、行動裝置、聊天等。 |

使用AEM Headless最適化Forms，您可以[在AEM中建立並發佈表單](create-and-publish-a-headless-form.md)一次；任何使用者端（React、Angular、原生行動裝置、聊天機器人）都可以[擷取表單JSON](architecture.md)，並使用該頻道的適當UI來轉譯。

### 為何應使用Headless表單，而非以UI為基礎的表單解決方案？

Headless表單最適合您下列需求：

* **設計系統一致性** — 使用您現有的元件和品牌，而不需對抗程式庫預設值。
* **多管道** — 網頁、行動裝置和其他接觸點的單一表單定義（請參閱[概觀](overview.md)）。
* **CMS — 或後端導向的表單** — 作者無需部署程式碼即可變更表單結構和規則；您的應用程式只會使用JSON。
* **架構彈性** - [AF-core](https://www.npmjs.com/package/@aemforms/af-core)程式庫與架構無關；提供React繫結是為了方便起見，但您可以為其他架構建立繫結。
* **後端功能** — 利用AEM Forms進行預填、驗證、提交、工作流程和Forms資料模型，而不鎖定至特定UI棧疊。

### 何時適合使用Headless方法？

在以下情況下使用Headless表單：

* 您擁有或想要強大的設計系統或元件庫。
* Forms是由非開發人員所撰寫（例如在CMS中），且必須在多個應用程式或管道中運作。
* 您需要跨網路、行動或其他使用者端的相同表單邏輯（驗證、規則）。
* 您想要將重新轉譯最小化，並且保持表單邏輯可獨立於UI測試。

發生下列情況時，請考慮包含UI的傳統表單庫：

* 您需要在單一Web應用程式中快速建立工作表單，而不在乎自訂UI或多通道。
* 您的團隊偏好僅在單一架構的程式碼中定義表單。

### 「無頭」只是流行語，還是能解決實際問題？

它解決了真正的架構問題：

* **分離關注點** — 表單結構、規則和驗證位於資料與邏輯層中；UI層只會轉譯和傳送使用者動作。 這可改善測試性和重複使用性。
* **管道獨立性** — 一個表單定義可以驅動不同的UI （例如React Web、React Native、Angular或語音）。 AEM Headless最適化Forms是針對下列用途而建置：[建置一次、跨React、SPA、Web、行動等傳送](overview.md)。
* **不使用程式碼編寫** — 商務使用者可以在[最適化表單編輯器](create-a-headless-adaptive-form.md)中變更欄位和規則；開發人員不需要重新部署內容變更。
* **與現有棧疊整合** — 您保留設計系統、狀態管理和路由；Headless層僅處理表單狀態、驗證和提交。

## 實作與技術問題 {#implementation-technical}

### Headless表單如何管理狀態？

在AEM Headless最適化Forms中，狀態是由&#x200B;**Forms Web SDK**&#x200B;管理：

* **商業規則處理器** — 接受表單JSON、管理欄位狀態，以及執行JSON中定義的規則和事件處理常式。
* **React繫結器** — 在控制器上提供掛接（例如`useRuleEngine`），讓React元件接收目前的狀態和處理常式；非React UI可以透過核心API使用相同的狀態。
* **狀態**&#x200B;包含欄位值、可見度、有效性以及表單模型中定義的任何自訂屬性。

您的UI元件會接收狀態和處理常式（例如`[state, handlers] = useRuleEngine(props)`）；您會從`state`轉譯，並在使用者互動時呼叫`handlers`。 執行階段會保持狀態與表單定義及規則同步。 請參閱[架構](architecture.md)和[使用自訂元件來轉譯Headless表單](developing-for-headless-forms-using-your-own-components.md)。

### Headless表單設定中的驗證如何運作？

驗證是表單邏輯層的一部分：

* **限制**&#x200B;是以JSON格式定義（例如必要、最小/最大、模式）。 Forms Web SDK套用這些限制並將驗證狀態（例如有效/無效、錯誤訊息）公開至您的元件。
* **使用者端驗證**&#x200B;已由SDK根據表單結構套用；您的UI從狀態顯示錯誤。
* **伺服器端驗證**&#x200B;可透過AEM API使用（例如驗證端點）；您可以在提交之前或期間進行驗證。

您未在UI中實作驗證邏輯，您只會顯示執行階段提供的驗證狀態和訊息。

### 我可以將Headless表單與結構描述驗證(Yup、Zod、Joi)整合嗎？

內建驗證由表單JSON限制驅動。 若要使用Yup、Zod、Joi或類似工具：

* 您可以從結構描述&#x200B;**衍生或產生** Headless最適化表單JSON （例如，將JSON結構描述轉換為JSON），讓一個真實來源同時驅動結構描述驗證和表單結構。
* 對於表單JSON以外的&#x200B;**自訂驗證**，您可以在事件處理常式中或在提交之前執行您自己的驗證程式(Yup/Zod/Joi)，並將結果推入表單狀態或區塊提交。 整合點是您用於狀態和提交的相同鉤點/API。

[最適化Forms規格](/help/assets/headless-adaptive-forms-specification.pdf)和[JSON公式](architecture.md)定義執行階段使用的規則和限制模型。

### 如何處理非同步驗證（例如使用者名稱可用性）？

非同步驗證可在應用程式層中實作：

* 使用表單JSON （若支援）中的&#x200B;**規則或事件處理常式**&#x200B;在欄位變更時觸發邏輯。
* 在您的&#x200B;**自訂元件**&#x200B;中，使用相同的狀態/處理常式掛接來呼叫您的後端（例如，使用者名稱可用性API），然後更新欄位的有效性或透過執行階段API或您在UI中顯示的本機狀態顯示錯誤。
* 或者，在模糊上或送出&#x200B;**之前執行檢查**，並在非同步檢查失敗時，使用自訂訊息將欄位狀態設定為無效。

確切的模式取決於您的應用程式如何與[商業規則處理器](architecture.md)和自訂元件整合。

### 如何使用Headless表單提交資料至API？

提交與UI脫離：

* **AEM提交動作** — 您在AEM中設定表單以提交至REST端點、電子郵件或整合（例如Microsoft Dynamics、Salesforce）。 表單透過AEM提交，可處理實際的HTTP/後端呼叫。 請參閱[使用事件處理及提交表單資料](use-events-to-handle-and-submit-form-data.md)。
* **使用者端送出** — 您的應用程式可以從執行階段狀態接聽送出或收集表單資料，並將其傳送至您自己的API。 [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)檔案清單、擷取、驗證、提交及追蹤提交狀態。
* **預填** — 可以透過REST端點或伺服器端預填資料，以便在載入表單時填入狀態。 請參閱[分鏡指令碼 — 預填範例](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)。

## UI和設計控制項 {#ui-design-control}

### 我可以對Headless表單使用我自己的設計系統或元件庫嗎？

可以。 這是Headless表單的核心優點。 使用AEM Headless最適化Forms：

* 您&#x200B;**將您自己的元件**&#x200B;對應至表單模型（依欄位型別或資源型別）。 請參閱[使用自訂元件來轉譯Headless表單](developing-for-headless-forms-using-your-own-components.md)和[使用Google Material UI React元件來轉譯Headless表單](use-google-material-ui-react-components-to-render-a-headless-form.md)。
* 執行階段提供&#x200B;**狀態和處理常式**；您的元件會使用您的設計系統轉譯並呼叫處理常式，讓表單邏輯保持同步。
* 您可以使用&#x200B;**React Spectrum**、Material UI、Chakra UI或任何自訂元件庫；[規格](/help/assets/headless-adaptive-forms-specification.pdf)可延伸用於自訂元件（例如Chakra UI、Vue.js）。 請參閱[常見問題集 — 自訂架構](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks)。

### Headless表單提供協助工具支援（ARIA、鍵盤處理）嗎？

協助工具已在您提供的&#x200B;**UI層**&#x200B;中實作。 Headless圖層不會轉譯DOM，因此不會單獨新增ARIA或鍵盤行為。 您可以透過以下方式取得協助工具：

* 使用設計系統或程式庫中的&#x200B;**可存取的元件** （許多包括ARIA和鍵盤支援）。
* 在您的自訂欄位元件（標籤、錯誤訊息、焦點管理、鍵盤導覽）中遵循&#x200B;**協助工具最佳實務**。
* 確保您收到的表單結構和狀態（例如必要、無效、可見）會反映在您的元件的ARIA屬性和行為中。

如果您使用現成可用的React Spectrum元件，即可運用其內建的協助工具。

### 我如何處理複雜的UI元件（日期選擇器、自訂下拉選單）？

將它們視為&#x200B;**自訂元件**，對應至對應的欄位型別或自訂資源型別，格式為JSON：

* 實作您的元件以接受與其他欄位元件相同的&#x200B;**prop/state/handlers** （例如，透過`useRuleEngine`）。
* 使用&#x200B;**狀態**&#x200B;來取得值、可見度和有效性；使用&#x200B;**處理常式**&#x200B;來更新值並觸發驗證。
* 使用您選擇的UI資料庫呈現您的日期選擇器或自訂下拉式清單；變更時，請使用新值呼叫處理常式，以便表單狀態保持正確。

請參閱[使用自訂元件來轉譯Headless表單](developing-for-headless-forms-using-your-own-components.md)，以依欄位型別和資源型別對應。

### 我可以動態新增或移除欄位（動態表單）嗎？

表單結構是由伺服器傳回的&#x200B;**表單JSON**&#x200B;所定義。 動態行為可透過以下方式取得：

* **JSON格式的規則** — 根據運算式顯示/隱藏、啟用/停用或設定值。 [商業規則處理器](architecture.md)會執行這些規則；您的元件會對`state.visible`等做出反應。
* **伺服器導向結構** — 不同的使用者或內容可以接收不同形式的JSON （例如，不同的步驟或區段），因此「動態」可以表示「每個請求都有不同的形式定義」。
* **使用者端變更** — 如果您的應用程式可以修改表單模型（例如，以可重複的結構新增/移除專案），執行階段可以反映這一點；確切的功能取決於表單結構描述和執行階段API。

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)包含動態行為範例。

### 我如何處理條件欄位（根據輸入顯示/隱藏）？

條件式可見性是由商業規則處理器評估的JSON格式的&#x200B;**規則**&#x200B;驅動。 您定義條件（例如「當欄位A等於X時，顯示欄位B」）；執行階段更新狀態（例如，`state.visible`）。 您的元件只需要&#x200B;**遵循狀態** （例如`if (!state.visible) return null;`）。 除了從狀態轉譯之外，顯示/隱藏不需要額外的UI邏輯。 階層式與條件式行為記錄在[最適化Forms規格](/help/assets/headless-adaptive-forms-specification.pdf)中，並在[Storybook — 階層式欄位](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType：drop-down；formJson.items[0].minimum：！undefined；formJson.items[0].maximum：！undefined；formJson.items[0].label.value：Choose+number+of+options；formJson.items[0].enum[0]：1；formJson.items[0].enum[1]：2；formJson.items[1].fieldType：drop)中示範。 另請參閱[常見問題集 — 階層式欄位](faq.md#do-headless-adaptive-forms-support-cascading-fields)。

## 效能與擴充性 {#performance-scalability}

### Headless表單的效能是否高於傳統表單庫？

雖然可行，但實作方式不同：

* **目標式更新** — 設計良好的Headless執行階段只會更新狀態並通知依賴它的元件，與整體式表單元件相比，可減少不必要的重新呈現。
* **較小的UI組合** — 您只出貨您使用的UI元件（您的設計系統），而非完整的程式庫元件集。
* **延遲載入** — 需要時可擷取表單JSON；初始套件組合可保持較小。

效能也取決於您實作元件的方式（例如，避免不必要的重新呈現、記憶）。

### 它們如何最小化重新呈現？

* **狀態圖形** — 執行階段會保持結構中的表單狀態，允許微調更新，所以只有受影響的樹狀結構部分才需要重新呈現。
* **掛接設計** — 類似`useRuleEngine`的掛接可以實作，以只將元件訂閱到它們使用的狀態，因此父項或同層級變更不會強制重新呈現每個欄位。
* **您的責任** — 您可以在自訂元件中使用React最佳實務（例如，`React.memo`、穩定的回呼），進一步將重新轉譯最小化。

### Headless表單是否適合用於大型多步驟表單？

可以，只要設計恰當：

* **表單定義** — 大型表單可以分割為JSON中的步驟或區段；只有可見的步驟/區段可能需要在UI中完全啟用，並且在支援隱藏區段的規則評估時會延遲。
* **狀態** — 執行階段有一個一致的表單狀態；步驟導覽只會顯示/隱藏區段，或更新「目前步驟」而不複製資料。
* **區塊和延遲載入** — 您可以在區塊中擷取表單JSON，或在步驟推進時載入其他區段，以保持初始裝載和剖析成本較低。

對於非常大型的表單，請考慮結構（例如精靈步驟）、伺服器驅動的表單變體，以及使用實際負載測量轉譯和規則執行。

## 整合與生態系統 {#integration-ecosystem}

### Headless表單可搭配Next.js / SSR /伺服器動作使用嗎？

* **Next.js / React** — 是。 React轉譯器和鉤子會在React環境中運作。 在使用者端元件中使用Forms Web SDK；視需要在伺服器或使用者端上從JSON擷取。
* **SSR** — 您可以在伺服器上擷取表單JSON，並將其傳遞給使用者端，使表單與資料水合。 表單互動（狀態、驗證、規則）會在載入SDK的使用者端上執行。 請避免在SSR期間轉譯依賴純使用者端狀態的表單欄位，或使用在使用者端上水合的預留位置。
* **伺服器動作(Next.js)** — 您可以從提交處理常式呼叫伺服器動作：當使用者提交時，您的使用者端程式碼會收集表單資料（從Headless狀態）並呼叫伺服器動作，而不是或除了AEM提交端點之外。

### Headless表單如何與CMS、Headless商務或後端系統整合？

* **CMS** - AEM是表單定義的CMS：作者建立和發佈表單JSON。 其他CMS可參考或連結至表單URL/API。 您的應用程式會從AEM （或CDN）擷取表單，並選擇從其他CMS提取副本或版面。
* **預填和提交** - [預填](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)和提交可以點選REST端點，因此您可以從CRM、DAM或商務後端預填和提交到相同或不同的系統。 AEM Forms也支援[Microsoft Dynamics和Salesforce](faq.md)、REST、電子郵件和自訂提交動作。
* **Forms資料模型** - AEM Forms提供Forms資料模型，可連線至不同的資料來源；Headless表單可使用這些功能進行預填、驗證和提交，而不需要您自行建立每個整合。

若為行動與離線案例，建議透過Headless最適化Forms API[&#128279;](mobile-forms-best-practices.md) 建置您自己的應用程式並擷取表單定義。

## 另請參閱 {#see-also}

* [概觀](overview.md)
* [架構](architecture.md)
* [常見問題](faq.md)
* [建立並發佈Headless表單](create-and-publish-a-headless-form.md)
* [Headless調適型表單API](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [程式碼遊樂場](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=en)
* [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
