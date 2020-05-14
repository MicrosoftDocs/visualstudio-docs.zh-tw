---
title: 如何:使用 ClickOnce 部署 API 以程式設計方式檢查應用程式更新 |微軟文件
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
ms.openlocfilehash: 5250e719cce945bdcce90a9d49d2ed8c27555612
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444956"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>如何：使用 ClickOnce 部署 API 以程式設計方式檢查應用程式更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 提供了兩種在部署應用程式後更新應用程式的方法。 在第一種方法中,您可以配置 ClickOnce 部署,以便在特定間隔內自動檢查更新。 在第二種方法中,可以編寫使用<xref:System.Deployment.Application.ApplicationDeployment>類根據事件(如使用者請求)檢查更新的代碼。  
  
 以下過程顯示了一些用於執行程式設計更新的代碼,並介紹了如何配置 ClickOnce 部署以啟用程式設計更新檢查。  
  
 為了以程式設計方式更新 ClickOnce 應用程式,必須指定更新的位置。 這有時稱為部署提供程式。 有關設定此屬性的詳細資訊,請參閱[選擇單擊更新原則](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
> [!NOTE]
> 您還可以使用下面描述的技術從一個位置部署應用程式,但從另一個位置更新應用程式。 有關詳細資訊,請參閱[如何:為部署更新指定備用位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)。  
  
### <a name="to-check-for-updates-programmatically"></a>以程式設計方式檢查更新  
  
1. 使用首選的命令列或可視工具創建新的 Windows 窗體應用程式。  
  
2. 建立您希望使用者選擇以檢查更新的任何按鈕、功能表項或其他使用者介面項。 從該專案的事件處理程式中,調用以下方法來檢查並安裝更新。  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. 編譯應用程式。  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 Mage.exe 部署以程式設計方式檢查更新的應用程式  
  
- 以在演練中解釋的使用 Mage.exe 部署應用程式的說明[:手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 呼叫 Mage.exe 生成部署清單時,請確保使用命令行`providerUrl`開關 ,並指定 ClickOnce 應檢查更新的 URL。 例如,如果應用程式將從`http://www.adatum.com/MyApp`中更新,則產生部署清單的調用可能如下所示:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 MageUI.exe 部署以程式設計方式檢查更新的應用程式  
  
- 以在演練中解釋的使用 Mage.exe 部署應用程式的說明[:手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 在 **「部署選項」** 選項卡上,將 **「開始位置」** 欄位設定為應用程式清單 ClickOnce 應檢查更新。 在「**更新選項**」選項卡上,清除**此應用程式應選中更新**複選框。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您的應用程式必須具有完全信任的許可權才能使用程式設計更新。  
  
## <a name="see-also"></a>另請參閱  
 [如何:設定更新指定備用位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [選擇點擊更新原則](../deployment/choosing-a-clickonce-update-strategy.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
