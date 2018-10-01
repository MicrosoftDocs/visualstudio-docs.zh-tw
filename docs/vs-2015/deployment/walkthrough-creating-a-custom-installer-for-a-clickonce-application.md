---
title: 逐步解說： 建立 ClickOnce 應用程式的自訂安裝 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2e544bf49437ce6e3c1e8de1b7c792c63a32700a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489776"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>逐步解說：為 ClickOnce 應用程式建立自訂安裝程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[逐步解說： 建立 ClickOnce 應用程式的自訂安裝程式](https://docs.microsoft.com/visualstudio/deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application)。  
  
任何.exe 檔案為基礎的 ClickOnce 應用程式將以無訊息方式安裝，並由自訂安裝程式更新。 自訂安裝程式可以實作自訂使用者體驗，在安裝期間，其中包括安全性和維護作業的自訂對話方塊。 若要執行安裝作業，自訂的安裝程式會使用<xref:System.Deployment.Application.InPlaceHostingManager>類別。 本逐步解說示範如何建立自訂安裝程式會以無訊息方式安裝 ClickOnce 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>若要建立自訂的 ClickOnce 應用程式安裝程式  
  
1.  在 ClickOnce 應用程式，加入到 System.Deployment 和 System.Windows.Forms 的參考。  
  
2.  將新類別新增至您的應用程式，並指定任何名稱。 本逐步解說會使用名稱`MyInstaller`。  
  
3.  新增下列`Imports`或`using`陳述式的新類別。  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  將下列方法新增至您類別中。  
  
     這些方法會呼叫<xref:System.Deployment.Application.InPlaceHostingManager>方法，以下載部署資訊清單中，判斷提示適當的權限，請安裝，然後下載並安裝到 ClickOnce 快取的應用程式權限的使用者。 自訂安裝程式可以指定 ClickOnce 應用程式預先信任，或可以延後信任決策<xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>方法呼叫。 此程式碼預先信任應用程式。  
  
    > [!NOTE]
    >  透過預先信任所指派的權限不能超過自訂安裝程式的程式碼的權限。  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5.  若要嘗試從您的程式碼的安裝，呼叫`InstallApplication`方法。 例如，如果名為您的類別`MyInstaller`，您可能會呼叫`InstallApplication`方式如下。  
  
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
 ClickOnce 應用程式也可以加入自訂更新邏輯，包括在更新程序時顯示的自訂使用者介面。 如需詳細資訊，請參閱<xref:System.Deployment.Application.UpdateCheckInfo>。 ClickOnce 應用程式也可以抑制標準的 [開始] 功能表項目、 捷徑，以及新增或移除程式項目使用`<customUX>`項目。 如需詳細資訊，請參閱 < [\<進入點 > 項目](../deployment/entrypoint-element-clickonce-application.md)和<xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [\<進入點 > 項目](../deployment/entrypoint-element-clickonce-application.md)



