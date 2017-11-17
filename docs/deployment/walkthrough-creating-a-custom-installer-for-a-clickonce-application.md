---
title: "逐步解說： 建立自訂安裝程式的 ClickOnce 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 3b6a7069b520c1c4834ee3ca1a5824660803a665
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>逐步解說：為 ClickOnce 應用程式建立自訂安裝程式
任何.exe 檔案為基礎的 ClickOnce 應用程式可以無訊息模式安裝並自訂安裝程式更新。 自訂安裝程式可以實作自訂的使用者經驗，在安裝期間，其中包括安全性和維護作業的自訂對話方塊。 若要執行安裝作業，自訂安裝程式會使用<xref:System.Deployment.Application.InPlaceHostingManager>類別。 本逐步解說示範如何建立自訂安裝程式會以無訊息方式安裝 ClickOnce 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>若要建立自訂的 ClickOnce 應用程式安裝程式  
  
1.  在 ClickOnce 應用程式，加入 System.Deployment 和 System.Windows.Forms 的參考。  
  
2.  將新類別加入您的應用程式，並指定任何名稱。 本逐步解說會使用名稱`MyInstaller`。  
  
3.  加入下列`Imports`或`using`陳述式加入新類別的頂端。  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  將下列方法加入至類別。  
  
     這些方法呼叫<xref:System.Deployment.Application.InPlaceHostingManager>下載部署資訊清單中，宣告適當的權限要求安裝，然後下載並安裝於 ClickOnce 快取應用程式權限的使用者。 自訂安裝程式可以指定 ClickOnce 應用程式預先受信任，或可以將信任決策延後<xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>方法呼叫。 此程式碼中預先信任應用程式。  
  
    > [!NOTE]
    >  只要預先信任指派的權限不能超過自訂安裝程式的程式碼的權限。  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  若要嘗試安裝您的程式碼，呼叫`InstallApplication`方法。 例如，如果您將類別命名為`MyInstaller`，您可能會呼叫`InstallApplication`方式如下。  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>後續步驟  
 ClickOnce 應用程式也可以加入自訂更新邏輯，包括自訂使用者介面，以在更新程序期間顯示。 如需詳細資訊，請參閱<xref:System.Deployment.Application.UpdateCheckInfo>。 ClickOnce 應用程式也可以抑制標準的開始功能表項目、 快速鍵，以及新增或移除程式項目使用`<customUX>`項目。 如需詳細資訊，請參閱[\<進入點 > 項目](../deployment/entrypoint-element-clickonce-application.md)和<xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [\<進入點 > 項目](../deployment/entrypoint-element-clickonce-application.md)