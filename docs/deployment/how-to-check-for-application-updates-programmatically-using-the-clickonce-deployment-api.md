---
title: 如何： 檢查以程式設計方式使用 ClickOnce 部署 API 的應用程式更新 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5953af7c6aafe914be409d8c3ab459b6b4261e54
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>如何：使用 ClickOnce 部署 API 以程式設計方式檢查應用程式更新
ClickOnce 會提供兩種方式，一旦部署之後，更新的應用程式。 在第一個方法中，您可以設定 ClickOnce 部署以自動檢查更新，在特定間隔內。 在第二個方法中，您可以撰寫程式碼乃使用<xref:System.Deployment.Application.ApplicationDeployment>檢查更新的類別，根據事件，例如使用者的要求。  
  
 下列程序顯示一些程式碼執行以程式設計方式更新，也會說明如何設定 ClickOnce 部署，啟用以程式設計方式更新檢查。  
  
 若要以程式設計方式更新 ClickOnce 應用程式，您必須指定更新的位置。 這有時也稱為部署提供者。 如需有關如何設定這個屬性的詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
> [!NOTE]
>  您也可以使用部署從一個位置的應用程式但只更新另一個如下所述的技巧。 如需詳細資訊，請參閱[How to： 指定部署更新的替代位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)。  
  
### <a name="to-check-for-updates-programmatically"></a>若要以程式設計方式檢查更新  
  
1.  建立新的 Windows Form 應用程式，使用您慣用的命令列或視覺效果工具。  
  
2.  建立按鈕、 功能表項目，或您想讓使用者選取檢查更新的其他使用者介面項目。 從該項目的事件處理常式，呼叫下列方法來檢查並安裝更新。  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  編譯您的應用程式。  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 Mage.exe 部署的應用程式，以程式設計方式檢查更新  
  
-   依照指示部署應用程式中所述，使用 Mage.exe[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 在呼叫 Mage.exe 來產生部署資訊清單，請務必使用命令列參數`providerUrl`，並指定 ClickOnce 在哪裡檢查更新檔的 URL。 如果您的應用程式將更新從[ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp)，比方說，您對產生的部署資訊清單的呼叫可能會看起來像這樣：  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 MageUI.exe 来部署的應用程式，以程式設計方式檢查更新  
  
-   依照指示部署應用程式中所述，使用 Mage.exe[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 在**部署選項**索引標籤上，設定**開始位置**應該檢查更新 ClickOnce 應用程式資訊清單的欄位。 在**更新選項**索引標籤上，清除**此應用程式應該檢查更新檔**核取方塊。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您的應用程式必須具有完全信任權限使用以程式設計方式更新。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 指定部署更新的替代位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)