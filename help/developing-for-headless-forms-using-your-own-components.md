---
title: 使用自訂元件轉譯Headless表單
description: 瞭解如何建立自訂元件，並將它們對應至Headless最適化Forms欄位。 本指南說明如何依欄位型別和資源型別對應元件，以達成自訂轉譯和行為。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 使用自訂元件轉譯Headless表單 {#developing-for-headless-forms-using-your-own-components}

在Headless最適化Forms中，您可以建立和實施自訂元件以定義表單的外觀和功能。 雖然預設元件提供標準行為，但您可能需要特定UI元素或互動，例如自訂「公告」元件或專用的「草寫簽名」欄位。

本文會引導您建立自訂React元件，並將其對應至您的Headless最適化表單。

## &#x200B;1. 建立自訂React元件

首先，建立將呈現表單欄位的React元件。 此元件可使用任何React程式庫（例如「材質UI」、「Ant設計」或您自己的自訂樣式）。

例如，讓我們建立自訂&#x200B;**宣告**&#x200B;元件，以特定樣式呈現唯讀訊息。

1. 導覽至React專案的元件目錄（例如`src/components`）。
2. 為您的元件建立新的資料夾和檔案，例如`Announcement/index.tsx`。
3. 實作元件。 它應該接受與Headless Forms執行階段相容的`props` （通常接收欄位的狀態）。

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. 對應自訂元件

若要使用自訂元件，您必須在`mappings.ts`檔案中對應該元件。 Headless Forms執行階段會使用此對應來決定要以JSON格式呈現每個欄位的React元件。

有兩種主要方式來對應元件：依&#x200B;**欄位型別**&#x200B;或依&#x200B;**資源型別**。

### 依欄位型別對應

標準對應是以表單JSON中的`fieldType`屬性為基礎（例如，`text-input`、`checkbox`、`button`）。 當您想要以自訂版本取代標準元件的&#x200B;*所有*&#x200B;執行個體時，這會很有用。

1. 開啟`src/utils/mappings.ts` （或定義對應的任何位置）。
2. 匯入您的自訂元件。
3. 使用`fieldType`做為索引鍵將其新增至對應物件。

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### 依資源型別對應（自訂元件）

如果您已在AEM中建立自訂元件（例如，擴充標準Text元件的「Announcement」元件），而且您只想在React應用程式中以不同方式轉譯&#x200B;*該特定元件*，則應該依照其&#x200B;**資源型別**&#x200B;或唯一的識別碼來對應它。

此方法可讓您正常呈現標準文字元件，而自訂「公告」元件會使用您專門的React實作。

1. 識別元件的唯一識別碼。 在Headless表單JSON中，這通常可在`:type`屬性中找到，或如果設定了自訂`fieldType`。
2. 使用此識別碼新增對應。

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **注意：**&#x200B;請確定您的AEM表單模型匯出正確的`:type`或識別碼，符合您在`mappings.ts`中使用的金鑰。

## &#x200B;3. 套用對應

最後，請確定您的Headless表單例項使用這些自訂對應。

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

依照這些步驟，您可以使用符合您特定設計和功能要求的元件來擴充Headless最適化Forms的功能。
