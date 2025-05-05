---
title: 使用核心元件和 Headless 建置吸引人的表單
seo-title: Build Engaging Forms Using Core Components and Headless
description: 使用核心元件和 Headless 建置吸引人的表單
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: bcc51bcae3b26cf20e7c0b5b75935bf69a991731
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 85%

---

# 在AEM Formsas a Cloud Service上使用核心元件和Headless最適化Forms打造引人入勝的Forms {#build-engaging-forms-using-core-components-and-headless}

## 實驗室概觀 {#lab-overview}

在這個實作實驗室中，您將學習：

如何運用 AEM Forms 使用與 AEM Sites 一致的最新核心元件輕鬆建立最適化表單，透過將最適化表單作為無頭表單交付到 Web、行動裝置和聊天來實施全通路資料擷取體驗。您還將學習有關樣式、自訂和前端開發的最佳實務。

## 關鍵重點 {#key-takeaways}

* **業務彈性**：作為業務使用者，我可以輕鬆地為多個通道建立表單體驗。

* **前端開發人員的力量**：作為前端開發人員，我可以使用無頭表單來控制終端使用者體驗。

* **開發人員速度**：作為一名開發人員，我可以輕鬆且一致地自訂 Sites 和 Forms 元件。

## 必備條件 {#prerequisites}

若要在實驗室中使用此手勢：

* 安裝[最新版本的Git](https://git-scm.com/downloads)。 若您為Git的新手，請參閱[安裝Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。

* 安裝[Node.js 16.13.0或更新版本](https://nodejs.org/en/download/)。 如果您是初次使用Node.js，請參閱[如何安裝Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)。

* [為您的Formsas a Cloud Service環境啟用最適化AEM Forms核心元件](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md)。

* 安裝[Microsoft Visual Studio Code](https://code.visualstudio.com/download)或任何純文字編輯器。 檔案中的範例使用Microsoft Visual Studio Code。



## 第一課 {#lesson-1}

### 目標 {#lesson-1-objectives}

熟悉 AEM Forms as a Cloud Service 環境。

### 課程內容 {#lesson-1-context}

在本課程中，您將瀏覽使用者介面，熟悉 AEM Forms as a Cloud Service 環境。

### 練習 {#lesson-1-excercise}

1. 打開瀏覽器並輸入 Cloud Service 編寫環境的 URL。例如：
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. 登入Cloud Service作者環境。
   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. 若要導覽至AEM Forms UI，請按一下&#x200B;**Forms > Forms和檔案**。



   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   關閉任何與偏好設定或資訊相關的快顯視窗。 顯示所有可用的表格。


## 第二課

### 目標

使用最新的核心元件編寫最適化表單，設定並提交表單。

### 課程內容

在本課中，作為業務使用者，您將使用最適化表單編寫和用於資料擷取的標準化 OOTB 核心元件，為 Web、移動和聊天等多個通道編寫最適化表單。

### 練習

1. 為表單建立一個提交端點：

   1. 在新的瀏覽器標籤中打開 <https://requestbin.com/>。
   1. 點選 **Create a public bin** 並複製端點 URL。

      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. 使用精靈介面編寫最適化表單：

   1. 在第 1 課中使用的瀏覽器標籤中，導覽至 AEM Forms as Cloud Service Web 介面，然後導覽至 Forms and Documents。

      ![](/help/assets/screenshot2028114029.png)

   1. 點選 **Create** 並選擇 Adaptive Form。

      ![](/help/assets/screenshot2028114629.png)

   1. 從範本選擇畫面中選擇 **Blank with Core Components** 範本，如下所示：

      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. 點選 **Style** 標籤，選擇&#x200B;**wknd-theme**&#x200B;主題，如下圖：

      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. 按一下&#x200B;**提交**&#x200B;標籤，然後選取&#x200B;**提交至REST端點**&#x200B;卡片，並在&#x200B;**URL中指定POST要求**&#x200B;欄位的公用Bin，如下所示：

      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. 按一下&#x200B;**建立**。為表單指定名稱和標題。例如，**註冊**。 按一下&#x200B;**建立**。

   1. 最適化表單編輯器打開。關閉任何與偏好設定或資訊相關的快顯視窗或對話框。按一下左側邊欄上的元件瀏覽器，然後分別將&#x200B;**Header**&#x200B;和&#x200B;**Footer**&#x200B;元件新增至空白表單的頂端和底部。

      ![](/help/assets/screenshot2028121929.png)

   1. 從「元件」瀏覽器拖放元件以建立表單，如下所示：

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}

1. 將驗證新增至表單：

   1. 點選&#x200B;**電話號碼**&#x200B;元件，快顯視窗選單隨即顯示。點擊選單中的&#x200B;**扳手圖示**&#x200B;以設定欄位。

   1. 打開&#x200B;**驗證標籤**，標記欄位&#x200B;**必要**，然後點擊&#x200B;**完成**。成功訊息隨即顯示。

      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. 預覽並提交表單。

   1. 點擊&#x200B;**預覽**，從終端使用者的角度預覽表單。

   1. 以虛擬資料填入表單。

   1. 提交表單。

      ![](/help/assets/screenshot2028125729.png)

   1. 在 Request Bin 標籤中，檢查提交的資料。

      ![](/help/assets/screenshot2028125829.png)

1. 新增互動性以使用規則表單：

   1. 按一下&#x200B;**核取方塊以接收5%折扣**&#x200B;元件。 在選項工具列上，按一下「規則」圖示。 「規則編輯器」選項隨即開啟。

   1. 建立規則，當選取&#x200B;**勾選接收5%折扣**&#x200B;選項的方塊時，套用信用卡的選項會停用。

1. Publish表單。

   1. 開啟AEM Forms管理介面，例如`https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`，然後選取表單。

   1. 點擊&#x200B;**發佈**。

      ![](/help/assets/screenshot2028115629.png)

      成功訊息隨即顯示。

      ![](/help/assets/screenshot2028115729.png)

      表單的發佈 URL 會類似於 `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`。

   1. 要查看已發佈的表單，請將上述 URL 中的程序 ID (pXXXXXX) 和環境 ID (eXXXXXX) 取代為您環境的 ID。

## 第三課

### 目標

使用前端開發最佳實務更新樣式。

### 課程內容

在本課中，作為前端開發人員，您將學習如何輕鬆地更新先前建立的最適化表單的樣式。

### 練習

設定主題的本機存放庫：

1. 使用管理員權限打開命令提示字元或殼層：

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 在命令提示字元中，使用以下命令瀏覽到 **c:\git** 資料夾

   ```Shell
   cd c:\git
   ```

1. 使用以下命令複製主題前端程式碼：

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. 按照列出的順序使用以下命令瀏覽到 **aem-forms-theme-canvas** 目錄並打開 Visual Studio Code。

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. 選取&#x200B;**信任上層資料夾中所有文件的作者**，並點選&#x200B;**是的，我信任作者**。

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. 要呈現在您的雲端服務發佈環境中託管的表單，請重新命名 `env_template` 文件。要重新命名檔案，請用右鍵按一下 **env_template** 檔案，然後選擇&#x200B;**重新命名**&#x200B;選項。

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. 為 .env 檔案中的變數設定以下值並儲存檔案：

   * **AEM_URL**：指定您的雲端服務發佈環境。例如 `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**：指定表單的路徑。例如，如果表單路徑為 `/content/forms/af/registration`，則此變數的值將為 `registration`。

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

1. 在AEM環境中建立本機使用者。

   >[!NOTE]
   > 若要建立本機使用者：
   > 前往`AEM Home` > `Tools` > `Security` > `Users`
   > 確定使用者是forms-users群組的成員。


1. 在命令提示字元視窗中，執行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * 如果您收到要求透過`npm notice Run npm nstall -g npm@9.6.0`命令更新npm的訊息，請忽略該訊息。
   > * 除非活頁簿中有指示，否則不要執行其他 npm 命令。

1. 現在執行以下命令來預覽表單。

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   執行上述命令後，請等候`webpack compiled`訊息，系統會將您重新導向至AEM登入頁面。

1. 在AEM登入頁面上按一下&#x200B;**本機登入（僅限管理員工作）**。
1. 輸入已建立本機使用者的認證，表單就會顯示在瀏覽器標籤中。

   >[!NOTE]
   >
   >如果您在執行 `npm run live` 命令超過 3-4 分鐘後瀏覽器出現黑畫面，請將瀏覽器 URL 中的 `localhost` 變更為 127.0.0.1，並點擊&#x200B;**輸入**。


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. 在 Visual Studio Code 中，打開 `PROJECT\src\site\_variables.scss` 檔案。請注意，`$error` 顏色是紅色陰影。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 在瀏覽器中，提交表單以在&#x200B;**名字**&#x200B;欄位中看到紅字。

   ![](/help/assets/screenshot2028120829.png)

1. 將 **$error** 顏色設定為 **#5736eb** 並儲存檔案。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 重新整理瀏覽器並提交表單。請注意，名字欄位上的錯誤顏色已跟著更改。

   ![](/help/assets/screenshot2028121129.png)

1. 在命令提示字元中，按 **CTRL+C**，輸入 **Y**，然後按 **Enter** 鍵終止 npm 程序。停止 npm 伺服器很重要，這樣就不會與下一組練習發生衝突。
1. 關閉 Visual Studio Code 和命令提示字元視窗。

## 第四課

### 目標

將表單作為無頭表單呈現在 Web/行動裝置和其他介面。

### 課程內容

在本課程中，作為前端開發人員，您將學習如何使用 React Spectrum 設計框架，將之前建立的最適化表單呈現為無頭表單。

### 練習

使用 React 啟動專案設定本機存放庫：

1. 使用管理員權限打開命令提示字元。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 在命令提示字元中，使用以下命令瀏覽到 **c:\git** 資料夾

   ```Shell
   cd c:\git
   ```

1. 使用以下命令複製最適化表單 React 啟動專案：

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

要呈現在您的雲端服務發佈環境中託管的表單：

1. 將 env_template 檔案重新命名為 .env 檔案。要重新命名，請用右鍵按一下 **env_template** 檔案，然後選擇&#x200B;**重新命名**&#x200B;選項。

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. 為 .env 檔案中的變數設定以下值。更新變數後，儲存檔案。

   * **AEM_URL**：指定雲端服務發佈環境的 URL。例如 `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**：指定上節課程所建最適化表單的路徑。例如 `/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. 打開命令視窗，確認您位於 react-starter-kit-aem-headless-forms 目錄中，然後執行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. 在命令提示字元視窗中，執行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   上面的命令會啟動本機開發伺服器，該伺服器將使用 react-spectrum 前端庫以無頭方式呈現從 AEM 擷取的表單定義。

   >[!NOTE]
   >
   > 
   > 如果您在執行 `npm start` 命令超過 3-4 分鐘後瀏覽器出現黑畫面，請將瀏覽器 URL 中的 `localhost` 變更為 127.0.0.1，並點擊&#x200B;**輸入**。

   ![](/help/assets/screenshot2028118229.png)

讓我們確認一下這種無頭形式的規則執行情況：

1. 選取&#x200B;**勾選此項以享受 5% 折扣**&#x200B;選項。隨後申請信用卡的選項會停用。

   ![](/help/assets/screenshot2028126229.png)

1. 取消選取&#x200B;**勾選此項以享受 5% 折扣**&#x200B;以啟用信用卡選項。

   ![](/help/assets/screenshot2028126329.png)

讓我們以業務使用者的身份對伺服器上的表單進行變更，並自動查看反映在無頭表單中的變更。

1. 在瀏覽器中打開 AEM Forms 管理介面。例如 [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments)。

1. 選取&#x200B;**contacts**&#x200B;表單，然後按一下&#x200B;**編輯。**&#x200B;這會在最適化表單編輯器中打開表單。


1. 選取&#x200B;**電話號碼**&#x200B;欄位，然後點選工具列中的&#x200B;**編輯圖示 (鉛筆圖示)**。如果您工具列沒有跳出來，請點擊右上角的&#x200B;**編輯**&#x200B;按鈕切換到編輯模式，然後點擊左上角的 **預覽**&#x200B;按鈕。

   ![](/help/assets/screenshot2028119629.png)

1. 將標籤變更為手機號碼。點擊表單中的任何空白區域將儲存對表單所做的變更。

   ![](/help/assets/screenshot2028119729.png)

讓我們發佈更新的表單以將變更散佈到發佈環境。

1. 在 AEM Forms 管理介面標籤中，選擇註冊表單，然後點擊&#x200B;**取消發佈**。如果您沒有看到&#x200B;**取消發佈**&#x200B;按鈕，請跳至第 3 步直接發佈變更。

1. 點擊&#x200B;**取消發佈**。在相應的對話框中點擊&#x200B;**關閉**。

1. 瀏覽器重新整理後，選擇註冊表單，然後點擊&#x200B;**發佈**。

1. 點擊&#x200B;**發佈**。在相應的對話框中點擊&#x200B;**關閉**。

1. 重新整理顯示無頭表單的瀏覽器標籤。請注意，電話號碼標籤已變更為手機號碼。

   ![](/help/assets/screenshot2028120529.png)

1. 打開用於啟動 **react-starter-kit-aem-headless-forms** 專案的命令提示字元視窗，**按 CTRL+C**，然後輸入 **Y**，並按 Enter 鍵終止 npm 程序。停止 npm 伺服器很重要，這樣就不會與下一組練習發生衝突。

1. 關閉 Visual Studio Code 和命令提示字元視窗。


## 第五課

### 目標

使用 Google Material UI 將表單呈現為無頭表單

### 課程內容

在本課程中，作為前端開發人員，您將學習如何使用 Google Material UI 將之前建立的最適化表單呈現為無頭表單。

### 練習

使用 Material UI 啟動專案設定本機存放庫：

1. 使用管理員權限打開命令提示字元。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. 在命令提示字元中，使用以下命令瀏覽到 **c:\git** 資料夾：

   ```Shell
   cd c:\git
   ```

1. 按列出的順序執行以下命令以建立名為 mui 的資料夾，並使用以下命令瀏覽到 mui 資料夾：

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 使用以下命令複製最適化表單 React 啟動專案：

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

要呈現在您的雲端服務發佈環境中託管的表單：

1. 將 **env_template** 檔案重新命名為 **.env** 檔案。要重新命名，請用右鍵按一下 **env_template** 檔案，然後選擇&#x200B;**重新命名**。

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. 為 .env 檔案中的變數設定以下值。更新變數後，儲存檔案。使用 **CTRL + S** 切換組合以儲存檔案。

   * **AEM_URL**：指定雲端服務發佈環境的 URL。例如 [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**：指定上節課程所建最適化表單的路徑。例如 /content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. 打開命令視窗，確認您位於 **react-starter-kit-aem-headless-forms** 目錄中，然後執行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. 在命令提示字元視窗中，執行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   該命令會啟動本機開發伺服器，並使用 Google Material UI 前端庫以無頭方式呈現從 AEM 擷取的表單定義。

   >[!NOTE]
   >
   >如果您在執行 `npm start` 命令超過 3-4 分鐘後瀏覽器出現黑畫面，請將瀏覽器 URL 中的 `localhost` 變更為 127.0.0.1，並點擊&#x200B;**輸入**。

   ![](/help/assets/screenshot2028127229.png)

1. 若要評估此表單轉譯中相同商業邏輯的執行情況：

   選取&#x200B;**勾選此項以享受 5% 折扣**。後續選項&#x200B;**您想申請 We Finance 公司信用卡表單嗎？**&#x200B;將會停用。

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## 第六課

### 目標

使用 Material UI 元件變體建立無頭表單的替代外觀

### 課程內容

在本課程中，作為前端開發人員，您將學習如何使用 Material UI 為業務使用者之前建立的最適化表單建立不同元件的替代外觀。

### 練習

更新無頭專案中元件的變體。將 Material UI 文字輸入元件的變體變更為 `OutlinedInput`：

1. 在 Visual Code 中，透過打開位於 `src/components/textinput/index.tsx` 的 `index.tsx` 檔案瀏覽到文字輸入元件。

1. 在程式碼 103 行的開頭新增 `//`。這會將行轉換為註解。

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 在第 104 行新增以下內容以使用不同的元件變體，然後儲存檔案。使用 **CTRL + S** 切換組合以儲存檔案。

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   &#39;OutlinedInput&#39; 變體必須使用正確的大寫字母，否則編譯會失敗。本機開發環境編譯會在命令提示字元中自動開始。等到您看到以下訊息

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 如果沒有自動重新整理，請手動重新整理瀏覽器，您就可以看到文字輸入元件使用不同的變體。

   ![](/help/assets/screenshot2028127729.png)


   此變更適用於終端使用者，無需對 AEM Forms Server 中的表單定義進行任何變更，且是針對考慮中的無頭通道。例如，本實驗室中的 Web 通道。

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. 關閉 Visual Studio Code 和命令提示字元視窗。

## 常見問題集 (FAQ)

+++ 最適化表單精靈是否已正式推出？

是的，AEM Forms as Cloud Service 已提供最適化表單精靈。

+++


+++ 核心元件是否已正式推出？

是的，AEM Forms as a Cloud Service 已提供 Adaptive Forms 核心元件。

+++

+++ Headless 表單是否已正式推出？

是的，AEM Forms as a Cloud Service 已提供 Headless 表單。

+++

+++ Headless 表單是否需要單獨授權？

不用，Headless 表單使用相同的授權值量度，即表單提交次數。

+++

+++ AEM 6.5 Forms 是否提供核心元件和 Headless 表單？

是的，AEM Forms 6.5 Service Pack 16 及更高版本均提供最適化表單核心元件和無頭表單。

+++


## 後續步驟

現在您已經了解如何建置最適化表單，並使用無頭表單將它們傳送到多個通道，接下來您應該嘗試將新技能付諸實踐。請繼續為您的終端使用者大規模建立和提供卓越的資料擷取體驗！

## 資源

* [最適化表單核心元件簡介](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [使用核心元件建立最適化表單](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [更新核心元件型 AF 的樣式](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless 最適化表單](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [使用 Headless React 入門套件](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)
