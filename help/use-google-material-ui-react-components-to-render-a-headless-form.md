---
title: 使用Google Material UI react元件來呈現Headless表單
description: 瞭解如何使用Google Material-UI React元件來呈現Headless表單。 本全方位指南將逐步引導您建立自訂Headless最適化Forms元件，以對應並使用Google Material-UI React元件來設定Headless最適化表單的樣式。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 476509d5-f4c1-4d1c-b124-4c278f67b1ef
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# 使用自訂react程式庫來轉譯Headless表單

您可以建立並實作自訂元件，以根據組織的需求和准則自訂Headless調適型表單的外觀和功能（行為）。

這些元件有兩個主要用途：控制表單欄位的外觀或樣式，以及在表單模型例項中儲存透過這些欄位收集的資料。 如果這聽起來令人困惑，請不要擔心 — 我們會儘快更詳細地探索這些目的。 現在，讓我們專注於建立自訂元件的初始步驟、使用這些元件呈現表單，以及使用事件儲存資料並將資料提交到REST端點。

在本教學課程中，Google素材UI元件用於示範如何使用自訂React元件來轉譯Headless調適型表單。 不過，此程式庫並無限制，您可自由使用任何React元件程式庫或開發自己的自訂元件。

根據本文的結論，在[使用入門套件](create-and-publish-a-headless-form.md)文章建立並發佈Headless表單中建立的&#x200B;_聯絡我們_&#x200B;表單將轉換為以下內容：

![](assets/headless-adaptive-form-with-google-material-ui-components.png)


使用Google素材UI元件呈現表單的主要步驟如下：

![](assets/headless-forms-graphics-source-main.svg)

## 1.安裝Google資料UI

依預設，入門套件使用[Adobe的Spectrum](https://spectrum.adobe.com/)元件。 讓我們設定為使用[Google的素材UI](https://mui.com/)：

1. 確認入門套件未執行。 若要停止入門套件，請開啟您的終端機，導覽至&#x200B;**react-starter-kit-aem-headless-forms**，然後按Ctrl-C (在Windows、Mac和Linux上相同)。

   請勿嘗試關閉終端機。 關閉終端機並不會停止入門套件。

1. 執行以下命令：

```shell
    
    npm install @mui/material @emotion/react @emotion/styled --force
    
```

它會安裝Google素材UI npm程式庫，並將程式庫新增至入門套件相依性。 您現在可以使用Material UI元件來呈現表單元件。


## 2.建立自訂React元件

讓我們建立自訂元件，該元件以[Google素材UI文字欄位](https://mui.com/material-ui/react-text-field/)元件取代預設的[文字輸入](https://spectrum.adobe.com/page/text-field/)元件。

Headless表單定義中使用的每個元件型別（[fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input)或：type）都需要個別元件。 例如，在您在上一節建立的「聯絡我們」表單中，型別為`text-input` ([fieldType： &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def))的「名稱」、「電子郵件」和「電話」欄位以及訊息欄位的型別為`multiline-input` ([&quot;fieldType&quot;： &quot;multiline-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/reference-json-properties-fieldtype--multiline-input))。


讓我們建立自訂元件，以覆蓋使用[fieldType： &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def)屬性和[原物料UI文字欄位](https://mui.com/material-ui/react-text-field/)元件的所有表單欄位。


若要建立自訂元件，並對應具有[fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def)屬性的自訂元件：

1. 在程式碼編輯器中開啟&#x200B;**react-starter-kit-aem-headless-forms**&#x200B;目錄，並導覽至`\react-starter-kit-aem-headless-forms\src\components`。


1. 建立&#x200B;**滑桿**&#x200B;或&#x200B;**RTF**&#x200B;資料夾的復本，並將複製的資料夾重新命名為&#x200B;**materialtextfield**。 Slider和RTF是啟動應用程式中可用的兩個範例自訂元件。 您可以使用這些專案建立自己的自訂元件。

   ![VSCode](/help/assets/richtext-custom-component-in-vscode.png)中的materialtextfield自訂元件

1. 開啟`\react-starter-kit-aem-headless-forms\src\components\materialtextfield\index.tsx`檔案，並將現有程式碼取代為下列程式碼。 此程式碼會傳回並轉譯[Google素材UI文字欄位](https://mui.com/material-ui/react-text-field/)元件。

```JavaScript
 
     import React from 'react';
     import {useRuleEngine} from '@aemforms/af-react-renderer';
     import {FieldJson, State} from '@aemforms/af-core';
     import { TextField } from '@mui/material';
     import Box from '@mui/material/Box';
     import { richTextString } from '@aemforms/af-react-components';
     import Typography from '@mui/material/Typography';


     const MaterialtextField = function (props: State<FieldJson>) {

         const [state, handlers] = useRuleEngine(props);

         return(

         <Box>
             <Typography component="legend">{state.visible ? richTextString(state?.label?.value): ""} </Typography>
             <TextField variant="filled"/>
         </Box>

         )
     }

     export default MaterialtextField;
```


`state.visible`零件會檢查元件是否設定為可見。 如果是，會使用`richTextString(state?.label?.value)`擷取並顯示欄位標籤。

![](/help/assets/material-text-field.png)


您的自訂元件`materialtextfield`已就緒。 讓我們設定此自訂元件，以Google素材UI文字欄位取代[fieldType： &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def)的所有執行個體。

## 3.對應具有Headless表單欄位的自訂元件

使用協力廠商程式庫元件來轉譯表單欄位的程式稱為對應。 您將每個([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input))對應到協力廠商程式庫的對應元件。

所有對應相關資訊都已新增至`mappings.ts`檔案。 `mappings.ts`檔案中的`...mappings`陳述式參考預設對應，其會以[Adobe頻譜](https://spectrum.adobe.com/page/text-field/)元件覆蓋（[fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input)或：type）。

若要為`materialtextfield`元件新增對應（在上一步中建立）：

1. 開啟`mappings.ts`檔案。

1. 新增下列匯入陳述式，將`materialtextfield`元件加入`mappings.ts`檔案：


   ```JavaScript
       import MaterialtextField from "../components/materialtextfield";
   ```

1. 新增下列陳述式，以將`text-input`與materialtextfield元件對應。


   ```JavaScript
       "text-input": MaterialtextField
   ```

   檔案的最終程式碼如下所示：

   ```JavaScript
         import { mappings } from "@aemforms/af-react-components";
         import MaterialtextField from "../components/materialtextfield";
   
   
         const customMappings: any = {
           ...mappings,
           "text-input": MaterialtextField
        };
        export default customMappings;
   ```

1. 儲存並執行應用程式。 表單的前三個欄位會使用[Google素材UI文字欄位](https://mui.com/material-ui/react-text-field/)轉譯：

   ![](assets/material-text-field-form-rendetion.png)


   同樣地，您可以建立訊息的自訂元件(「fieldType」：「multiline-input」)，並為服務(「fieldType」：「number-input」)欄位評分。 您可以複製下列Git存放庫作為訊息的自訂元件，並為服務欄位評分：

   [https://github.com/singhkh/react-starter-kit-aem-headless-forms](https://github.com/singhkh/react-starter-kit-aem-headless-forms)

## 下一步

您已成功轉譯包含使用Google材質UI之自訂元件的表單。 您是否嘗試透過按一下提交按鈕(與對應的Google原物料UI元件對應)來提交表單？ 如果沒有，請繼續嘗試。

表單會將資料提交至任何資料來源嗎？ 沒有？ 別擔心。 這是因為您的表單未設定為與執行階段程式庫通訊。

如何設定表單以與其通訊？ 我們即將推出文章，詳細說明所有內容。 敬請期待！
