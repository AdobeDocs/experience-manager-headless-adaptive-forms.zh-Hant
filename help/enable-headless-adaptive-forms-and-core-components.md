---
title: 在AEM 6.5 Forms上啟用Headless最適化Forms
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM 6.5 Forms
description: 瞭解如何使用我們的逐步指南，在AEM 6.5 Forms上啟用Headless調適型表單。 我們的教學課程會逐步引導您完成此程式，讓您輕鬆將此強大功能整合至您的網站，並改善您的使用者體驗。
seo-description: Learn how to enable headless adaptive forms on AEM 6.5 Forms with our step-by-step guide. Our tutorial walks you through the process, making it easy to integrate this powerful feature into your website and improve your user experience.
contentOwner: Khushwant Singh
role: Admin
exl-id: e1a5e7e0-d445-4cca-b8d7-693d9531f075
source-git-commit: d791daa149d0380b03bb6ba9776db47440feea02
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 12%

---

# 在AEM 6.5 Forms上啟用Headless最適化Forms {#enable-headless-adaptive-forms-on-aem-65-forms}

若要在您的AEM 6.5 Forms環境中啟用Headless最適化Forms，請設定AEM Archetype 41或更新版本的專案，並將其部署至您的所有製作和發佈執行個體。

將AEM Archetype 41或更新版本的專案部署到AEM 6.5 Forms執行個體後，您就可以[建立以核心元件為基礎的最適化Forms](create-a-headless-adaptive-form.md)。 這些表單以JSON格式表示，並當作Headful和Headless最適化Forms使用，以便在包括行動、網頁和原生應用程式在內的一系列管道中提供更大的彈性和自訂。

## 先決條件 {#prerequisites}

在AEM 6.5 Forms環境中啟用Headless最適化Forms之前，

* [升級至AEM 6.5 Forms Service Pack 16 (6.5.16.0)或更新版本](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=zh-Hant)。

* 安裝最新版的[Apache Maven](https://maven.apache.org/download.cgi)。

* 安裝純文字編輯器。 例如，Microsoft Visual Studio Code。

## 建立及部署最新的AEM原型專案

若要建立以AEM Archetype 41或[稍後](https://github.com/adobe/aem-project-archetype)為基礎的專案，並將其部署至您的所有作者與發佈執行個體：

1. 以管理員身分登入電腦，託管並執行AEM 6.5 Forms執行個體。
1. 開啟命令提示或終端機。
1. 執行以下命令，建立以AEM Archetype 41為基礎的專案：

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.23" 
   ```

   * Linux或Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.23" 
   ```

   執行上述命令時，請務必考慮以下事項：

   * 更新命令以反映環境的特定值，包括appTitle、appId和groupId。 此外，請將includeFormsenrollment的值設為「y」。 如果您使用Forms入口網站，請設定&#x200B;_includeExamples=y_&#x200B;選項，將Forms入口網站核心元件納入您的專案中。


1. （僅適用於以Archetype版本41為基礎的專案）在AEM Archetype專案建立後，請啟用以核心元件為基礎的最適化Forms的主題。 若要啟用主題：

   1. 開啟[AEM原型專案資料夾]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html以進行編輯：

   1. 在第21行新增下列程式碼：

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![在第21](/help/assets/code-to-enable-themes.png)行新增上述程式碼

   1. 儲存並關閉檔案。

1. 更新專案以包含最新版Forms核心元件：

   1. 開啟[AEM原型專案資料夾]/pom.xml以進行編輯。
   1. 將`core.forms.components.version`和`core.forms.components.af.version`的版本設定為[最新的Forms核心元件](https://github.com/adobe/aem-core-forms-components/tree/release/650)版本。

   1. 儲存並關閉檔案。


1. 成功建立AEM原型專案後，為您的環境建置部署套件。 若要建置套件：

   1. 導覽至AEM Archetype專案的根目錄。


   1. 執行以下命令，為您的環境建置AEM原型專案：

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](assets/corecomponent-build-successful.png)


   成功建立AEM原型專案後，就會產生AEM套件。 您可以在[AEM原型專案資料夾]\all\target\[appid].all-[version].zip中找到該套件

1. 使用[封裝管理員](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=zh-Hant)，在所有製作和發佈執行個體上部署[AEM Archetype專案資料夾]\all\target\[appid].all-[version].zip封裝。

>[!NOTE]
>
>
>
>如果您在透過封裝管理員存取發佈執行個體的登入對話方塊時遇到困難，請嘗試透過下列URL登入： http://[發佈伺服器URL]：[連線埠]/系統/主控台。 這可讓您登入發佈執行個體，讓您繼續安裝程式。


核心元件已針對您的環境啟用。 將空白的Core Components based Adaptive Form範本和Canvas 3.0主題部署到您的環境，讓您能夠[建立Core Components based Adaptive Forms](create-a-headless-adaptive-form.md)。

## 常見問答

### 核心元件有哪些？

[核心元件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=zh-Hant) 是一組適用於 AEM 的標準化網站內容管理 (WCM) 元件，可加快開發時間並降低網站的維護成本。

### 啟用核心元件時新增了哪些功能？


當為您的環境啟用調適型表單核心元件時，一個以核心元件為主的調適型表單空白範本和 Canvas 3.0 主題會新增至您的環境中。為您的環境啟用調適型表單核心元件後，您可以：

* 建立以最適化Forms為基礎的核心元件。
* 建立以核心元件為基礎的最適化表單範本。
* 建立核心元件型最適化表單範本的自訂主題。
* 為行動、網路、原生應用程式等需要表單Headless呈現的管道和服務提供核心元件型最適化表單的JSON呈現。
