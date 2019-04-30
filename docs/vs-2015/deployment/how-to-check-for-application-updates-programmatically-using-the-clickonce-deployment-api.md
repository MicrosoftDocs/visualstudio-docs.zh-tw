---
title: HOW TO：檢查以程式設計方式使用 ClickOnce 部署 API 的應用程式更新 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c713b9e2fe78f8e9c499c1af5e60a21fd3aea13
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442163"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>HOW TO：檢查以程式設計方式使用 ClickOnce 部署 API 的應用程式更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 提供兩種方式可在部署之後，更新的應用程式。 在第一個方法中，您可以設定 ClickOnce 部署，自動檢查更新，在特定時間間隔。 在第二個方法中，您可以撰寫程式碼使用<xref:System.Deployment.Application.ApplicationDeployment>檢查是否有更新的類別，根據事件，例如使用者的要求。  
  
 下列程序示範一些程式碼執行以程式設計方式更新，並也會說明如何設定 ClickOnce 部署以啟用程式設計方式更新檢查。  
  
 若要以程式設計方式更新 ClickOnce 應用程式，您必須指定更新的位置。 這有時候稱為部署提供者。 如需有關如何設定這個屬性的詳細資訊，請參閱 <<c0> [ 選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
> [!NOTE]
> 您也可以使用如下所述來部署您的應用程式，從一個位置，但從另一個更新它的技術。 如需詳細資訊，請參閱[如何：指定部署更新的替代位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)。  
  
### <a name="to-check-for-updates-programmatically"></a>若要以程式設計方式檢查更新  
  
1. 建立新的 Windows Forms 應用程式，使用您慣用的命令列或視覺效果工具。  
  
2. 建立按鈕、 功能表項目，或您希望使用者選取，以檢查有更新的其他使用者介面項目。 從該項目的事件處理常式，呼叫下列方法來檢查並安裝更新。  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. 編譯您的應用程式。  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 Mage.exe 會更新以程式設計方式檢查應用程式部署  
  
- 請依照下列指示來部署您的應用程式中所述，使用 Mage.exe[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 在呼叫 Mage.exe 來產生部署資訊清單，請務必使用命令列參數`providerUrl`，並指定 ClickOnce 在哪裡檢查更新檔的 URL。 如果您的應用程式會從更新[ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp)，比方說，您的呼叫，以產生部署資訊清單可能會看起來像這樣：  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 MageUI.exe 部署的應用程式，以程式設計方式檢查更新  
  
- 請依照下列指示來部署您的應用程式中所述，使用 Mage.exe[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 在 **部署選項**索引標籤上，設定**開始位置**ClickOnce 應該檢查更新的應用程式資訊清單的欄位。 在 **更新選項**索引標籤上，清除**此應用程式應該檢查更新檔**核取方塊。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您的應用程式必須使用以程式設計方式更新的完全信任權限。  
  
## <a name="see-also"></a>另請參閱  
 [如何：指定部署更新的替代位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
