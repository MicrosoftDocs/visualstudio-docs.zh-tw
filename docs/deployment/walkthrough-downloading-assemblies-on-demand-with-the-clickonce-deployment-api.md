---
title: "逐步解說：依 ClickOnce 部署 API 的要求下載組件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "組件, 下載 [ClickOnce]"
  - "ClickOnce 部署, 視需要下載"
  - "視需要下載的組件, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# 逐步解說：依 ClickOnce 部署 API 的要求下載組件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據預設，在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式中包含的所有組件，都會在應用程式首次執行時下載。  不過，您的應用程式可能有些部分是由一小群使用者使用。  在此情況下，只有在建立一種類型的組件時，才需要下載組件。  下列逐步解說會示範如何將應用程式中的某些組件標記為「選擇項」，以及如何在 Common Language Runtime \(CLR\) 要求這些組件時，使用 <xref:System.Deployment.Application> 命名空間中的類別來下載這些組件。  
  
> [!NOTE]
>  您的應用程式需要在完全信任的狀態下執行，才能使用這個程序。  
  
## 必要條件  
 您將需要下列其中一個元件才能完成這個逐步解說：  
  
-   Windows SDK。  Windows SDK 可從 Microsoft 下載中心下載。  
  
-   Visual Studio。  
  
## 建立專案  
  
#### 建立使用視需要下載組件的專案  
  
1.  建立名為 ClickOnceOnDemand 的目錄。  
  
2.  開啟 Windows SDK 命令提示字元，或是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令提示字元。  
  
3.  切換到 ClickOnceOnDemand 目錄。  
  
4.  使用下列命令產生公開\/私密金鑰組：  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  使用 \[記事本\] 或其他文字編輯器，定義名為 `DynamicClass`，並具有名為 `Message` 單一屬性的類別。  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  根據您使用的語言，以名為 `ClickOnceLibrary.cs` 或 `ClickOnceLibrary.vb` 的檔案將文字儲存到 ClickOnceOnDemand 目錄。  
  
7.  將此檔案編譯為組件。  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  若要取得組件的公開金鑰語彙基元，請使用下列命令：  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. 使用文字編輯器建立新的檔案，並輸入下列程式碼。  這個程式碼會建立 Windows Form 應用程式，該應用程式會在需要時下載 ClickOnceLibrary 組件。  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. 在程式碼中，尋找 <xref:System.Reflection.Assembly.LoadFile%2A> 的呼叫。  
  
11. 將 `PublicKeyToken` 設為您之前擷取的值。  
  
12. 將檔案儲存為 `Form1.cs` 或 `Form1.vb`。  
  
13. 使用下列命令將它編譯為可執行檔。  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## 將組件標記為選擇項  
  
#### 使用 MageUI.exe 將 ClickOnce 應用程式中的組件標記為選擇項  
  
1.  使用 MageUI.exe，建立應用程式資訊清單，如[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中所述。  請使用下列應用程式資訊清單的設定：  
  
    -   將應用程式資訊清單命名為 `ClickOnceOnDemand`。  
  
    -   在 \[**檔案**\] 頁面上的 \[ClickOnceLibrary.dll\] 資料列，將 \[**檔案類型**\] 欄設為 \[**無**\]。  
  
    -   在 \[**檔案**\] 頁面上 \[ClickOnceLibrary.dll\] 資料列的 \[**群組**\] 欄中，輸入 `ClickOnceLibrary.dll`。  
  
2.  使用 MageUI.exe，建立部署資訊清單，如[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中所述。  請使用下列部署資訊清單的設定：  
  
    -   將部署資訊清單命名為 `ClickOnceOnDemand`。  
  
## 測試新組件  
  
#### 若要測試視需要下載的組件  
  
1.  將您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署上載至 Web 伺服器。  
  
2.  輸入部署資訊清單的 URL，以便從 Web 瀏覽器啟動以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的應用程式。  如果您呼叫 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式 `ClickOnceOnDemand`，並將它上載至 adatum.com 的根目錄，您的 URL 會如下所示：  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  當您的主表單出現時，按下 <xref:System.Windows.Forms.Button>。  您應該會看到在訊息方塊視窗中顯示 "Hello, World\!" 的字串。  
  
## 請參閱  
 <xref:System.Deployment.Application.ApplicationDeployment>