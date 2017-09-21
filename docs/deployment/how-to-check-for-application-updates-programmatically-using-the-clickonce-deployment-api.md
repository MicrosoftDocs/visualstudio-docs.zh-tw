---
title: "如何：使用 ClickOnce 部署 API 以程式設計方式檢查應用程式更新 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "應用程式更新"
  - "ClickOnce 部署, 更新"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：使用 ClickOnce 部署 API 以程式設計方式檢查應用程式更新
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 提供可在部署應用程式時進行更新的兩種方式。  若使用第一種方法，您可以設定 ClickOnce 部署在某些間隔時間自動檢查更新；  若使用第二種方法，您可以撰寫使用 <xref:System.Deployment.Application.ApplicationDeployment> 類別的程式碼，以便根據事件 \(如使用者要求\) 檢查更新。  
  
 下列程序會示範某些用來執行程式設計方式更新的程式碼，同時也說明如何設定 ClickOnce 部署，使其以程式設計方式檢查更新。  
  
 如果要以程式設計的方式更新 ClickOnce 應用程式，必須指定更新的位置。  有時稱為部署提供者。  如需設定這項屬性的詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
> [!NOTE]
>  您也可以使用如下所述的技巧，從某個位置部署您的應用程式，但是從另一個位置進行更新。  如需詳細資訊，請參閱 [如何：指定部署更新的其他位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)。  
  
### 若要以程式設計方式檢查更新  
  
1.  使用偏好的命令列或視覺化工具建立新的 Windows Form 應用程式。  
  
2.  建立按鈕、功能表項目或其他使用者介面項目，讓使用者選取該項目即可檢查更新。  從該項目的事件處理常式中，呼叫下列方法，以檢查及安裝更新。  
  
     [!CODE [ClickOnceAPI#6](../CodeSnippet/VS_Snippets_Winforms/ClickOnceAPI#6)]  
  
3.  編譯應用程式。  
  
### 使用 Mage.exe 部署以程式設計方式檢查更新的應用程式  
  
-   請遵循[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中說明的指示，使用 Mage.exe 部署您的應用程式。  在呼叫 Mage.exe 產生部署資訊清單時，請務必使用命令列參數 `providerUrl`，並指定 ClickOnce 應前往檢查更新的 URL。  例如，如果您的應用程式會從 [http:\/\/www.adatum.com\/MyApp](http://www.adatum.com/MyApp) 進行更新，則用來產生部署資訊清單的呼叫可能如下所示：  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### 使用 MageUI.exe 來部署以程式設計方式檢查更新的應用程式  
  
-   請遵循[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中說明的指示，使用 Mage.exe 部署您的應用程式。  在 \[**部署選項**\] 索引標籤上，將 \[**開始位置**\] 欄位設定為 ClickOnce 應檢查更新的應用程式資訊清單。  在 \[**更新選項**\] 索引標籤上，清除 \[**此應用程式應該檢查更新檔**\] 核取方塊。  
  
## .NET Framework 安全性  
 您的應用程式必須具有完全信任的權限，才能使用程式設計方式的更新。  
  
## 請參閱  
 [如何：指定部署更新的其他位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)