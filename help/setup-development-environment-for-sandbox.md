---
title: 設定Forms as a Cloud Service沙箱的開發環境
description: 設定Forms as a Cloud Service沙箱的開發環境。
hide: true
exl-id: befac9ad-d2c4-4705-96fc-f0ea0ef823b8
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 0%

---

# 在Cloud Service上設定Headless最適化表單的開發環境

<span class="preview">此文章是&#x200B;**進行中的工作**.</span>


準備好在Cloud Service上建置和測試Headless最適化表單了嗎？ 為您的Cloud Service程式啟用Forms並開始。

## 開始之前

* 在本機電腦上安裝[最新版的Git](https://git-scm.com/downloads)。 若您為Git的新手，請參閱[安裝Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。 您可以使用Git存放庫將在本機開發環境中開發的表單和自訂程式碼推送到Cloud Service開發環境。

* 在本機電腦上安裝[Node.js 16.13.0或更新版本](https://nodejs.org/en/download/)。<!-- URL IS 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.org/en/learn/how-to-install-nodejs). -->


* 建立AEM as a Cloud Service方案：按照[建立方案](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program)文章的步驟1-7為您的組織建立方案。

* 為您的Cloud Service方案[啟用](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/prerelease#cloud-environments)發行前通道。

## 設定工作流程

若要在您的Forms as a Cloud Service沙箱上啟用Headless最適化表單，請為您的AEM Cloud Service方案啟用`Forms - Digital enrolment`解決方案。 然後，在本機電腦上建立Archetype 37或更新版本的專案，並將其推送至您的Forms as a Cloud Service環境。 完整的程式為：

![為Forms as a Cloud Service沙箱設定開發環境的工作流程](assets/FORMS-HLAF-SANDBOX-PRODUCTION-ENR.png)

### 1.為您的程式啟用Forms

<table style="table-layout:auto">
<tr>
  <td>
  1.登入<a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a>並選取<b> Experience Manager </b>選項。
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2.若為<b> Cloud Manager </b>選項，請按一下<b>啟動。 </b>您組織的計劃清單隨即顯示。
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3.針對您的程式，點選……圖示，然後選取<b>編輯程式</b>選項。 對話方塊隨即顯示。 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/edit-program.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    4.在[編輯程式]對話方塊中，移至[解決方案和附加元件]索引標籤<b>，選取[2] Forms - [數位註冊] </b>選項，然後點選[4] [更新] <b>。</b><b></b> 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/program-solution-addons.png">
    </a>
    <br>
  </td>
</tr>
</table>

### 2.將程式的Git存放庫複製到本機電腦

每個AEM as a Cloud Service程式都有一個Git存放庫。 它可讓您將自訂程式碼和資產從本機電腦上傳到您的Cloud Service環境。 在設定期間，Adobe會使用Git存放庫，從本機電腦將Headless最適化表單的相關程式碼、範本和其他資訊帶入Cloud Service程式。 在本機電腦上複製Cloud Service Git存放庫，是將自訂程式碼和內容從本機電腦帶到Cloud Service的第一步。

>[!INFO]
>
> 您一律可以認可至Git存放庫，不必加以複製。 但是，它有它自己的怪癖。 因此，本檔案將使用複製方法。


複製存放庫：

<table style="table-layout:fixed">
<tr>
  <td>
  1.在您的程式的管道方塊中，點選<b>存取存放庫資訊。 </b>會顯示包含存放庫資訊的對話方塊 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/git-repo.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2.點選<b>產生密碼</b>並複製<b>存放庫URL。</b> 
  </td>
  <td>
      <img alt="AEM as a Cloud Service計畫" src="assets/repository-info.png">
    <br>
  </td>
</tr>
<tr>
  <td>
    3.在本機電腦上，開啟命令提示字元、建立資料夾，然後執行下列命令，並提供存放庫認證（已要求）：
    </br>
    <code> git clone [Repository URL] </code> </br></br>
    例如， </br> 
    <code> git clone https://git.cloudmanager.adobe.com/stage-aemformsdev/khushwantsingh-p45413-uk89613/ </code>

</br>詢問時，請從<b>存放庫資訊</b>畫面取得<b>使用者名稱</b>和<b>密碼</b>。
</td>
  <td>
     <img alt="AEM as a Cloud Service計畫" src="assets/clone-success.png">
  </td>
</tr>
</table>


### 3.建立以AEM原型為主的專案

原型專案是以Maven為基礎的範本。 它會根據最佳實務來建立最低限度的專案，以開始使用Headless調適型表單。 此外，還包括Forms as a Cloud Service的Headless最適化表單核心功能。 必須建立和部署原型37或更新版本的專案。
®®®
視作業系統而定，執行maven命令以建立Experience Manager Forms as a Cloud Service專案。 使用原型版本37或更新版本。 請參閱[Archetype檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/developing/archetype/overview)以尋找最新版的Archetype。

+++ Microsoft® Windows

1. 以系統管理員許可權開啟命令提示字元（以系統管理員身分執行命令提示字元或bash shell）。
1. 執行以下命令：

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
     -D archetypeGroupId=com.adobe.aem ^
     -D archetypeArtifactId=aem-project-archetype ^
     -D archetypeVersion=37 ^
     -D appTitle=myheadlessform ^
     -D appId=myheadlessform ^
     -D groupId=com.myheadlessform ^
     -D includeFormsenrollment="y" ^
     -D includeFormsheadless="y" 
   ```

™™™

* 設定`appTitle`以定義標題和元件群組。
* 設定`appId`以定義Maven artifactId、元件、設定和內容資料夾名稱以及使用者端資料庫名稱。
* 設定`groupId`以定義Maven groupId和Java™ Source套件。
* 使用`includeFormsenrollment=y`選項來包含建立Adaptive Forms所需的Forms特定設定、主題、範本、核心元件和相依性。
* 使用`includeFormsheadless=y`選項加入Forms核心元件和加入Headless最適化表單功能所需的相依性。 啟用此選項時，會包含下列專案：
   * 含有&#x200B;**核心元件**&#x200B;的[Blank with core components](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/introduction)範本。
   * 前端React模組`ui.frontend.react.forms.af`。 它可協助您在react應用程式中轉譯Headless最適化表單。

+++®®®


+++ Apple macOS或Linux®

1. 以root使用者的身分開啟終端機。 它可讓您以管理許可權執行命令。 您也可以在開啟終端機視窗後使用`sudo root`命令，以管理許可權執行命令。
1. 執行以下命令：

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
     -D archetypeGroupId=com.adobe.aem \
     -D archetypeArtifactId=aem-project-archetype \
     -D archetypeVersion=37 \
     -D appTitle=myheadlessform \
     -D appId=myheadlessform \
     -D groupId=com.myheadlessform \
     -D includeFormsenrollment="y" \
     -D includeFormsheadless="y"  
   ```

™™™
* 設定`appTitle`以定義標題和元件群組。
* 設定`appId`以定義Maven artifactId、元件、設定、內容資料夾名稱和使用者端資料庫名稱。
* 設定`groupId`以定義Maven groupId和Java™ Source套件。
* 使用`includeFormsenrollment=y`選項來包含建立Adaptive Forms所需的Forms特定設定、主題、範本、核心元件和相依性。
* 使用`includeFormsheadless=y`選項加入Forms核心元件和加入Headless最適化表單功能所需的相依性。 啟用此選項時，會包含下列專案：
   * 含有&#x200B;**核心元件**&#x200B;的[Blank with core components](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/introduction)範本。
   * 前端回應模組`ui.frontend.react.forms.af`。 它可協助您在react應用程式中轉譯Headless最適化表單。

+++

命令成功完成時，會建立在`appID`中指定的專案資料夾。 例如，如果您使用值為`appID`的`myheadlessform`，則會建立名為`myheadlessform`的資料夾。 它包含以原型為基礎的專案。

### 4.將AEM原型專案推送至您的Cloud Service環境

1. 將Git存放庫的內容取代為Archtype型專案上的內容。

   >[!VIDEO](https://video.tv.adobe.com/v/3409809/)

1. 開啟命令提示字元，導覽至您的Git存放庫資料夾，然後依下列順序執行下列命令，將取代的內容上傳至您的Cloud Service環境。 您也可以使用視覺化編輯器，而不使用下列命令將內容推送到Cloud Service存放庫。

   ```
      git add .
      git commit
      git push origin
   ```

### 5.為您的程式執行建置管道



<table style="table-layout:auto">
<tr>
  <td>
  1.登入<a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a>並選取<b> Experience Manager </b>選項。
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2.若為<b> Cloud Manager </b>選項，請按一下<b>啟動。 </b>您組織的計劃清單隨即顯示。 開啟您的程式。 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3.針對您的管道，點選……圖示，然後選取<b>執行</b>選項。 如果系統提示您執行管道，請點選<b>執行</b>並等候管道<b>狀態</b>變更為<b>已完成</b>。  
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="AEM as a Cloud Service計畫" src="assets/run-build-pipeline.png">
    </a>
    <br>
  </td>
</tr>
</table>

現在，您的環境已準備好使用Headless最適化表單。 您現在可以將表單的JSON定義上傳至您的Cloud Service環境。 接著，根據此表單建立Headless調適型表單，並使用[getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition/operation/getForm)和其他rest API在您應用程式或服務中使用Headless調適型表單。
