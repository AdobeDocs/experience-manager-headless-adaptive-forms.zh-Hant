---
title: 在AEM Formsas a Cloud Service啟用Headless最適化Forms
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: 瞭解如何透過我們的逐步指南，在AEM Forms上啟用Headless調適型表單as a Cloud Service。 我們的教學課程將引導您完成整個程序，讓您可以輕鬆地為您的 AEM Forms 環境啟用這項強大功能。
seo-description: Learn how to enable headless adaptive forms on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 64%

---

# 在AEM Formsas a Cloud Service啟用Headless最適化Forms {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

在AEM Formsas a Cloud Service上啟用Headless最適化Forms，可讓您開始建立、發佈及傳送Headless Forms，使用您的AEM FormsCloud Service例項至多個管道。 您需要啟用調適型表單核心元件的環境才能使用 Headless 調適型表單。

## 考量事項

* 當您建立全新的AEM Formsas a Cloud Service程式時，[已針對您的環境啟用Headless最適化Forms](#are-adaptive-forms-core-components-enabled-for-my-environment)。

* 如果您有較舊版的 Forms as a Cloud Service 方案，且其中核心元件[未啟用](#enable-components)時，你可以[將調適型表單核心元件的相依性新增](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment)至您的 AEM as a Cloud Service 存放庫，並將該存放庫部署到您的 Cloud Service 環境以啟用 Headless 調適型表單。

* 如果您的現有Cloud Service環境提供[建立以核心元件為基礎的最適化Forms](create-a-headless-adaptive-form.md)的選項，表示已針對您的環境啟用Headless最適化Forms，而您可以將核心元件為基礎的最適化Forms當作Headless表單提供給需要最適化Forms的Headless呈現的行動裝置、網頁、原生應用程式和服務等管道。


>[!NOTE]
>
>
> Adobe提供最適化Forms [入門套件（React應用程式）](create-and-publish-a-headless-form.md)，以協助開發人員快速開始進行Headless最適化Forms開發，而不需在AEM Formsas a Cloud Service環境中啟用Headless最適化Forms。 您稍後可以透過[快速動手開發Headless表單](create-and-publish-a-headless-form.md)，在Formsas a Cloud Service環境中啟用Headless最適化Forms。

## 為AEM Formsas a Cloud Service環境啟用Headless最適化Forms

以所列順序執行以下步驟，為AEM Formsas a Cloud Service環境啟用Headless最適化Forms


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. 原地複製您的 AEM Forms as a Cloud Service Git 存放庫 {#clone-git-repository}

1. 登入 [Cloud Manager](https://my.cloudmanager.adobe.com/)，並選取您的組織和計劃。

1. 從&#x200B;**計劃總覽**&#x200B;頁面瀏覽至&#x200B;**管道**&#x200B;卡，按一下「**存取存放庫資訊**」按鈕，以存取和管理您的 Git 存放庫。 此頁面包括以下資訊：

   * Cloud Manager Git 存放庫的 URL。
   * Git 存儲庫認證 (使用者名稱和密碼) Git 使用者名稱。

   按一下「**生成密碼**」，查看或生成密碼。

1. 在本機電腦上開啟終端或命令提示並執行以下命令：

   ```Shell
   git clone [Git Repository URL]
   ```

   出現提示時，提供認證。 原地複製 存放庫至本機電腦。


## 2. 將調適型核心元件的相依性新增至您的 Git 存放庫 {#add-adaptive-forms-core-components-dependencies}

1. 在純文字程式碼編輯器中開啟 Git 存放庫資料夾。 例如 VS Code。
1. 閇啟 `[AEM Repository Folder]\pom.xml` 檔案進行編輯。
1. 以[核心元件文件](https://github.com/adobe/aem-core-forms-components)中指定的版本取代 `core.forms.components.version`、`core.forms.components.af.version` 和 `core.wcm.components.version` 等版本元件。如果該元件不存在，請新增這些元件。

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![提及最新版本的表單核心元件](/help/assets/latest-forms-component-version.png)

1. 在 `[AEM Repository Folder]\pom.xml` 檔案的相依性部份中，新增以下相依性並儲存檔案。

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. 開啟 `[AEM Repository Folder]/all/pom.xml` 檔案進行編輯。 在 `<embeddeds>` 部份新增以下相依性並儲存檔案。

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  以您的 appld 取代 `${appId}`。
   >
   >  若要尋找你的 `${appId}` (在 `[AEM Repository Folder]/all/pom.xml` 檔案內)，搜尋 `-packages/application/install` 一詞。在 `-packages/application/install` 一詞以前的文字是您的 `${appId}`。 例如，以下程式碼 `myheadlessform` 是 `${appId}`。
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. 在 `[AEM Repository Folder]/all/pom.xml` 檔案的 `<dependencies>` 部份中，新增以下相依性並儲存檔案：

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. 開啟 `[AEM Repository Folder]/ui.apps/pom.xml` 進行編輯。 新增 `af-core bundle` 相依性並儲存檔案。

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >確保您的專案中不包含以下調適型表單核心元件的成品。
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > 和
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. 儲存並關閉檔案。

## 3.更新專案以包含最新版Forms核心元件：

1. 開啟[AEM原型專案資料夾]/pom.xml進行編輯。


1. 儲存並關閉檔案。

## 4.將更新提交到您的Git存放庫並執行管道以部署存放庫 {#Commit-the-updates-to-your-git-repository}

1. 若要將程式碼認可到您的Git存放庫：
   1. 開啟終端機或命令提示。
   1. 瀏覽至您的 `[AEM Repository Folder]`，並依所列順序執行以下命令

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. 將檔案提交到 Git 存放庫後，[執行管道](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=zh-Hant)。

   執行好管道後，為對應環境啟用調適型表單核心元件。 此外，調適型表單 (核心元件) 範本和 Canvas 3.0 主題新增至您的 Forms as a Cloud Service 環境中，為您提供自訂和建以核心元件為主調適型表單的選項。


## 常見問答 {#faq}

### 核心元件有哪些？ {#core-components}

[核心元件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=zh-Hant) 是一組適用於 AEM 的標準化網站內容管理 (WCM) 元件，可加快開發時間並降低網站的維護成本。

### 啟用核心元件時新增哪些功能？ {#core-components-capabilities}

當為您的環境啟用調適型表單核心元件時，一個以核心元件為主的調適型表單空白範本和 Canvas 3.0 主題會新增至您的環境中。為您的環境啟用調適型表單核心元件後，您可以：

* 建立以最適化Forms為基礎的核心元件。
* 建立以核心元件為基礎的最適化表單範本。
* 建立核心元件型最適化表單範本的自訂主題。
* 為行動、網路、原生應用程式等需要表單Headless呈現的管道和服務提供核心元件型最適化表單的JSON呈現。

### 系統是否已為我的環境啟用調適型表單核心元件？ {#enable-components}

若要查看系統是否已為您的環境啟用調適型表單核心元件：

1. [原地複製您的 AEM Forms as a Cloud Service 存放庫](#1-clone-your-aem-forms-as-a-cloud-service-git-repository)。

1. 開啟您 AEM Forms Cloud Service Git 存放庫的 `[AEM Repository Folder]/all/pom.xml` 檔案。

1. 搜尋以下相依性：

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![尋找 core-forms-components-af-core artifact in all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   若相依性存在，表示系統已為您的環境啟用調適型表單核心元件。
