---
title: 使用核心元件和 Headless 建置吸引人的表單
description: 使用核心元件和Headless打造引人入勝的Forms。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 40%

---

# 在AEM 6.5 Forms上使用核心元件和Headless最適化Forms打造引人入勝的Forms {#build-engaging-forms-using-core-components-and-headless}

<!-- This article and many others in this entire repo are completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you take the time to add the required missing image ALT tags.  -->

## 實驗室概觀 {#lab-overview}

在這個實作實驗室中，您將瞭解如何使用AEM Forms搭配最新核心元件(與AEM Sites搭配使用)來快速建立調適型表單。 將這些表單作為Headless體驗傳送至Web、行動和聊天頻道，以實現無縫的全通道資料擷取。 您還將學習有關樣式、自訂和前端開發的最佳實務。

## 關鍵重點 {#key-takeaways}

* **業務彈性**：作為業務使用者，我可以輕鬆地為多個通道建立表單體驗。

* **前端開發人員的力量**：作為前端開發人員，我可以使用無頭表單來控制終端使用者體驗。

* **開發人員速度**：作為一名開發人員，我可以輕鬆且一致地自訂 Sites 和 Forms 元件。

## 開始之前 {#pre-requisites}

若要使用本實作實驗室：

* 安裝[最新版本的Git](https://git-scm.com/downloads)。 若您為Git的新手，請參閱[安裝Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。

* 安裝[Node.js 16.13.0或更新版本](https://nodejs.org/en/download/)。<!-- URL IS 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).-->

* [在您的AEM 6.5 Forms環境中啟用Headless最適化Forms](enable-headless-adaptive-forms-and-core-components.md)。

* 安裝[Microsoft Visual Studio Code](https://code.visualstudio.com/download)或任何純文字編輯器。 本檔案中的範例使用Microsoft Visual Studio Code。

## 第一課 {#lesson-1}

### 目標 {#lesson-1-objectives}

熟悉AEM 6.5 Forms環境。

### 課程內容 {#lesson-1-context}

在本課程中，您需透過導覽使用者介面來熟悉AEM 6.5 Forms。

### 練習 {#lesson-1-excercise}

1. 開啟瀏覽器，然後輸入作者環境的URL。 例如：
   [https://localhost:4502](https://localhost:4502)。

1. 登入後，瀏覽至 AEM Forms UI。點擊 **Forms**。

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. 點擊&#x200B;**表單和文件**。關閉任何與偏好設定或資訊相關的快顯視窗。

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   顯示所有可用的表格。

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## 第二課

### 目標

使用最新核心元件製作最適化表單、設定並提交表單。

### 課程內容

身為企業使用者，您將使用最適化Forms編輯器及其現成可用的核心元件來建置最適化表單。 然後，您可以將表單傳送至網路、行動和聊天頻道，以擷取資料。

### 練習

1. 為表單建立一個提交端點：

   1. 在新的瀏覽器標籤中打開 <https://pipedream.com/requestbin>。

      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. 點選 **Create a public bin** 並複製端點 URL。

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   此特定端點可作為提交和檢視資料的範例。 在實際生產中，您會使用自己的端點或資料來源來儲存擷取的資料。

1. 撰寫最適化表單：

   1. 在第1課使用的瀏覽器標籤中，導覽至AEM Forms網頁介面，並導覽至&#x200B;**Forms** > **Forms和檔案**。

   1. 點選 **Create** 並選擇 Adaptive Form。

      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. 從範本選取畫面選取&#x200B;**Blank with Core Components**&#x200B;範本，如下所示，然後按一下&#x200B;**下一步**。

      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. 指定`Contact us`作為表單的&#x200B;**標題**。 確定表單的&#x200B;**名稱**&#x200B;是`contact-us`。

      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. 按一下「**建立**」。隨即顯示對話方塊。

   1. 在對話方塊中，按一下&#x200B;**編輯**。 表單會在最適化表單編輯器中開啟。 關閉任何快顯視窗或對話方塊，以取得偏好設定或資訊。

   1. 開啟「元件」瀏覽器，並將「面板」元件拖放至畫面中央。

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. 從「元件」瀏覽器拖放元件以建立表單，如下所示：

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. 開啟「內容瀏覽器」，按一下「指南容器」屬性圖示，然後開啟&#x200B;**提交**&#x200B;標籤。

   1. 選取&#x200B;**提交至REST端點**&#x200B;提交動作

   1. 選取&#x200B;**啟用POST要求**&#x200B;選項，並在&#x200B;**POST要求的URL**&#x200B;文字方塊中指定第2課所建立的REST端點，然後按一下&#x200B;**完成**&#x200B;圖示。

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. 發佈最適化表單：

   1. 開啟AEM UI，導覽至&#x200B;**Forms** > **Forms與檔案**。 選取在上一步建立的表單，然後按一下&#x200B;**`Publish`**。

   1. 在&#x200B;**發佈Assets**&#x200B;對話方塊中，按一下&#x200B;**發佈**。 成功訊息隨即顯示。

## 第三課

### 目標

使用前端開發最佳實務更新樣式。

### 課程內容

在本課程中，身為前端開發人員，您將瞭解如何輕鬆更新先前建立的最適化表單的樣式。

### 練習

設定主題的本機存放庫：

1. 使用管理員權限打開命令提示字元或殼層：

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 在命令提示字元上，使用以下命令來瀏覽至`c:\git`資料夾。

   ```Shell
   cd git
   ```

   如果資料夾不存在，請使用`md git`命令來建立它。

1. 使用以下命令複製主題前端程式碼：

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. 按照列出的順序使用以下命令瀏覽到 **aem-forms-theme-canvas** 目錄並打開 Visual Studio Code。

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. 選取&#x200B;**信任上層資料夾中所有文件的作者**，並點選&#x200B;**是的，我信任作者**。

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. 將`env_template`檔案重新命名為.env。  要重新命名檔案，請用右鍵按一下 **env_template** 檔案，然後選擇&#x200B;**重新命名**&#x200B;選項。

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. 為.env檔案中的變數設定下列值，並儲存檔案：

   * **AEM_URL**：指定&#x200B;**發佈**&#x200B;執行個體的URL。 例如 `https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**：指定表單的名稱。 例如，`contact-us`。

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. 在命令提示字元視窗中，執行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * 如果您收到要求透過`npm`命令更新`npm notice Run npm nstall -g npm@9.6.0`的訊息，請忽略該訊息。
   > * 除非在活頁簿中指示您，否則請勿執行其他`npm`命令。

1. 現在，執行以下命令來預覽表單。

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   執行上述命令後，等待 `webpack compiled` 訊息。表單會顯示在瀏覽器標籤中。

   >[!NOTE]
   >
   >如果您在執行`npm run live`命令超過3-4分鐘後，在瀏覽器中遇到空白熒幕，請將瀏覽器URL中的`localhost`變更為127.0.0.1並按&#x200B;**Enter**。


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. 在 Visual Studio Code 中，打開 `PROJECT\src\site\_variables.scss` 檔案。請注意，`$error` 顏色是紅色陰影。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 在瀏覽器中，提交表單以在&#x200B;**名字**&#x200B;欄位中看到紅字。

   ![](/help/assets/error-color-before.png)

1. 將 **$error** 顏色設定為 **#5736eb** 並儲存檔案。

1. 重新整理瀏覽器並提交表單。請注意，名字欄位上的錯誤顏色已相應變更。

   ![](/help/assets/error-color-after.png)

1. 在命令提示字元中，按&#x200B;**CTRL+C**，輸入&#x200B;**Y**，然後按&#x200B;**Enter**&#x200B;鍵終止npm程式。 停止 npm 伺服器很重要，這樣就不會與下一組練習發生衝突。
1. 關閉 Visual Studio Code 和命令提示字元視窗。

## 第四課

### 目標

將表單轉譯為Headless表單以供Web/行動和其他介面使用。

### 課程內容

在本課程中，身為前端開發人員，您將瞭解如何使用React頻譜設計架構將先前建立的Adaptive Form轉譯為Headless表單。

### 練習

使用React入門專案設定本機存放庫：

1. 使用管理員權限打開命令提示字元。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. 在命令提示字元上，使用以下命令來瀏覽至`c:\git`資料夾。

   ```Shell
   cd git
   ```

1. 使用以下命令來複製調適型表單react入門專案：

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. 按照列出的順序使用以下命令瀏覽到 **react-starter-kit-aem-headless-forms** 目錄，並打開 Visual Studio Code。

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   Visual Studio Code 視窗隨即開啟。

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

若要轉譯託管在您的發佈環境中的表單：

1. 將env_template檔案重新命名為.env檔案。 要重新命名，請用右鍵按一下 **env_template** 檔案，然後選擇&#x200B;**重新命名**&#x200B;選項。

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. 為 .env 檔案中的變數設定以下值。更新變數後，儲存檔案。

   * **AEM_URL**：指定發佈環境的URL。 例如 `https://localhost:4503/`

   * **AEM_FORM_PATH**：指定在上一課中建立的最適化表單的路徑。 例如 `/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. 打開命令視窗，確認您位於 **react-starter-kit-aem-headless-forms** 目錄中，然後執行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. 在命令提示字元視窗中，執行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   上面的命令會啟動本機開發伺服器，該伺服器將使用 react-spectrum 前端庫以無頭方式呈現從 AEM 擷取的表單定義。

   >[!NOTE]
   >
   > 
   > 如果您在執行`npm start`命令超過3-4分鐘後，在瀏覽器中遇到空白熒幕，請將瀏覽器URL中的`localhost`變更為127.0.0.1並按&#x200B;**Enter**。

   ![](/help/assets/headless-adaptive-form-lab.png)

讓我們以業務使用者的身份對伺服器上的表單進行變更，並自動查看反映在無頭表單中的變更。

1. 在瀏覽器中打開 AEM Forms 管理介面。例如，[http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments)。

1. 選取&#x200B;**連絡我們**&#x200B;表單，然後按一下&#x200B;**編輯。**&#x200B;它會在最適化Forms編輯器中開啟表單。


1. 選取&#x200B;**聯絡電話**&#x200B;欄位，然後按一下工具列中的&#x200B;**編輯圖示（鉛筆圖示）**。 如果您看不到彈出式工具列，請切換到編輯模式。 按一下&#x200B;**預覽**&#x200B;按鈕右上角的&#x200B;**編輯**&#x200B;按鈕。

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. 將標籤變更為&#x200B;**行動電話號碼**。 點擊表單中的任何空白區域將儲存對表單所做的變更。

讓我們發佈更新的表單，以將變更傳播到已發佈的環境。

1. 在AEM Forms管理介面標籤中，選取與我們聯絡表單，然後按一下&#x200B;**取消發佈**。 如果您沒有看到&#x200B;**取消發佈**&#x200B;按鈕，請跳至第 3 步直接發佈變更。


1. 點擊&#x200B;**取消發佈**。在相應的對話框中點擊&#x200B;**關閉**。

1. 瀏覽器重新整理後，請選取與我們連絡的表單，然後按一下&#x200B;**發佈**。


1. 點擊&#x200B;**發佈**。在相應的對話框中點擊&#x200B;**關閉**。

1. 重新整理顯示無頭表單的瀏覽器標籤。請注意，聯絡人號碼標籤已變更為行動電話號碼。

   ![](/help/assets/headless-adaptive-form.png)

1. 打開用於啟動 **react-starter-kit-aem-headless-forms** 專案的命令提示字元視窗，**按 CTRL+C**，然後輸入 **Y**，並按 Enter 鍵終止 npm 程序。停止 npm 伺服器很重要，這樣就不會與下一組練習發生衝突。

1. 關閉 Visual Studio Code 和命令提示字元視窗。


## 第五課

### 目標

使用 Google Material UI 將表單呈現為無頭表單

### 課程內容

在本課程中，身為前端開發人員，您將瞭解如何使用Google資料UI將先前建立的最適化表單轉譯為Headless表單。

### 練習

使用原物料UI入門專案設定本機存放庫：

1. 使用管理員權限打開命令提示字元。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. 在命令提示字元上，使用以下命令來瀏覽至`c:\git`資料夾。

   ```Shell
   cd git
   ```

1. 依照列出的順序執行下列命令，以建立名為`mui`的資料夾，並使用下列命令導覽至`mui`資料夾：

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 使用以下命令來複製調適型表單react入門專案：

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. 按照列出的順序使用以下命令瀏覽到 **react-starter-kit-aem-headless-forms** 資料夾，並打開 Visual Studio Code 中的程式碼：

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

若要轉譯託管在您的發佈環境中的表單：

1. 將&#x200B;**env_template**&#x200B;檔案重新命名為&#x200B;**.env**&#x200B;檔案。 要重新命名，請用右鍵按一下 **env_template** 檔案，然後選擇&#x200B;**重新命名**。

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. 為 .env 檔案中的變數設定以下值。更新變數後，儲存檔案。 使用 **CTRL + S** 切換組合以儲存檔案。

   * **AEM_URL**：指定發佈環境的URL。 例如，[https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**：指定在上一課中建立的最適化表單的路徑。 例如，/content/forms/af/contact-us/


1. 打開命令視窗，確認您位於 **react-starter-kit-aem-headless-forms** 目錄中，然後執行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. 在命令提示字元視窗中，執行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   該命令會啟動本機開發伺服器，並使用AEM素材UI前端程式庫，以Headless方式呈現從Google擷取的表單定義。

   >[!NOTE]
   >
   >如果您在執行`npm start`命令超過3-4分鐘後，在瀏覽器中遇到空白熒幕，請將瀏覽器URL中的`localhost`變更為127.0.0.1並按&#x200B;**Enter**。

   ![](/help/assets/google-mui-form.png)

## 第六課

### 目標

使用 Material UI 元件變體建立無頭表單的替代外觀

### 課程內容

身為前端開發人員，您將在本課程中瞭解如何建立各種元件的替代資料UI版本。 您也將套用至業務使用者先前建立的最適化表單。

### 練習

更新無頭專案中元件的變體。將 Material UI 文字輸入元件的變體變更為 `OutlinedInput`：

1. 在 Visual Code 中，透過打開位於 `src/components/textinput/index.tsx` 的 `index.tsx` 檔案瀏覽到文字輸入元件。

1. 在程式碼 104 行的開頭新增 `//`。這會將行轉換為註解。

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 在第105行新增以下內容以使用元件的不同變體並儲存檔案。 使用 **CTRL + S** 切換組合以儲存檔案。

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   必須對「OverridedInput」變體使用正確的大小寫，否則編譯會失敗。 本機開發環境編譯會在命令提示字元中自動開始。等到您看到以下訊息

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 重新整理瀏覽器（如果未自動重新整理）以檢視文字輸入元件使用不同的變體。

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   此變更適用於終端使用者，無需對 AEM Forms Server 中的表單定義進行任何變更，且是針對考慮中的無頭通道。例如，本實驗中的網路管道。

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. 關閉 Visual Studio Code 和命令提示字元視窗。

## 常見問題集 (FAQ)

+++ 核心元件是否可公開使用？

是，最適化Forms核心元件可與AEM 6.5 Forms和Forms as Cloud Service搭配使用。 您需要AEM Forms 6.5 Service Pack 16或更新版本，才能使用最適化Forms核心元件。

+++

+++ Headless 表單是否需要單獨授權？

不用，Headless 表單使用相同的授權值量度，即表單提交次數。

+++




## 後續步驟

您現在知道如何建立最適化表單，並透過Headless表單跨管道傳送它們。 無論您的使用者身在何處，都可使用這些技能建立可擴充、高品質的資料擷取體驗。

## 資源

* [最適化表單核心元件簡介](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/adaptive-forms/introduction)

* [使用核心元件建立最適化表單](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components)

* [更新核心元件型 AF 的樣式](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components)

* [Headless最適化Forms](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-headless-adaptive-forms/using/overview)

* [使用Headless React入門套件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form)
