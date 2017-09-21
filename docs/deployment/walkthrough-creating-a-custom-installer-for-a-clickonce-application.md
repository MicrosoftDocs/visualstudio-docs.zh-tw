---
title: "逐步解說：為 ClickOnce 應用程式建立自訂安裝程式 | Microsoft Docs"
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
  - "ClickOnce 部署, 自訂安裝程式"
  - "自訂安裝程式 [ClickOnce]"
  - "部署應用程式 [ClickOnce], 自訂安裝程式"
  - "InPlaceHostingManager [ClickOnce], 自訂安裝程式"
  - "安裝程式 [ClickOnce], 自訂"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# 逐步解說：為 ClickOnce 應用程式建立自訂安裝程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

任何以 .exe 檔案為基礎的 ClickOnce 應用程式，都可以透過自訂安裝程式，以無訊息方式進行安裝及更新。  自訂安裝程式可以在安裝期間實作自訂的使用者經驗，包括安全性和維護作業的自訂對話方塊。  若要執行安裝作業，自訂安裝程式會使用 <xref:System.Deployment.Application.InPlaceHostingManager> 類別。  這個逐步解說示範如何建立以無訊息方式安裝 ClickOnce 應用程式的自訂安裝程式。  
  
## 必要條件  
  
### 若要建立自訂 ClickOnce 應用程式安裝程式  
  
1.  在您的 ClickOnce 應用程式中，加入 System.Deployment 和 System.Windows.Forms 的參考。  
  
2.  將新類別加入至應用程式中，並且指定任何名稱。  在本逐步解說中會使用名稱 `MyInstaller`。  
  
3.  將下列 `Imports` 或 `using` 陳述式加入至新類別的頂端。  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  將下列方法加入至類別。  
  
     這些方法會呼叫 <xref:System.Deployment.Application.InPlaceHostingManager> 方法，以下載部署資訊清單、判斷提示適當的權限、要求使用者提供安裝所需權限，然後下載應用程式並將它安裝至 ClickOnce 快取。  自訂安裝程式可以指定 ClickOnce 應用程式為預先信任，或將信任決策延後至 <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> 方法呼叫。  此程式碼會預先信任應用程式。  
  
    > [!NOTE]
    >  預先信任所指派的權限不能超過自訂安裝程式之程式碼的權限。  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  若要從您的程式碼嘗試安裝，請呼叫 `InstallApplication` 方法。  例如，如果您將類別命名為 `MyInstaller`，可透過下列方式呼叫 `InstallApplication`。  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## 後續步驟  
 ClickOnce 應用程式也可以加入自訂更新邏輯，包括更新程序期間顯示的自訂使用者介面。  如需詳細資訊，請參閱 <xref:System.Deployment.Application.UpdateCheckInfo>。  ClickOnce 應用程式也可以透過使用 `<customUX>` 項目，隱藏標準 \[開始\] 功能表項目、捷徑，以及 \[新增或移除程式\] 項目。  如需詳細資訊，請參閱 [\<entryPoint\> 項目](../deployment/entrypoint-element-clickonce-application.md)和 <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>。  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint\> 項目](../deployment/entrypoint-element-clickonce-application.md)