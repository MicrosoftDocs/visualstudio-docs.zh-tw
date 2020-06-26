---
title: 使用 ClickOnce 部署 API 自動更新應用程式
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6aee738d972b7c6e8c857ae87bb25758d871fe28
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382571"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>How to: Check for application updates programmatically using the ClickOnce deployment AP (如何：使用 ClickOnce 部署 API 以程式設計方式檢查應用程式更新)
ClickOnce 提供兩種方式，可在應用程式部署後進行更新。 在第一個方法中，您可以將 ClickOnce 部署設定為在特定間隔自動檢查更新。 在第二個方法中，您可以撰寫程式碼，使用 <xref:System.Deployment.Application.ApplicationDeployment> 類別根據事件（例如使用者要求）來檢查更新。

 下列程式顯示執行程式設計更新的一些程式碼，同時描述如何設定 ClickOnce 部署以啟用程式設計更新檢查。

 為了以程式設計方式更新 ClickOnce 應用程式，您必須指定更新的位置。 這有時稱為「部署提供者」。 如需有關設定此屬性的詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。

> [!NOTE]
> 您也可以使用以下所述的技術，從一個位置部署您的應用程式，但從另一個位置進行更新。 如需詳細資訊，請參閱[如何：指定部署更新的替代位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)。

### <a name="to-check-for-updates-programmatically"></a>以程式設計方式檢查更新

1. 使用您慣用的命令列或視覺效果工具，建立新的 Windows Forms 應用程式。

2. 建立您想要讓使用者選取來檢查更新的任何按鈕、功能表項目或其他使用者介面專案。 從該專案的事件處理常式，呼叫下列方法來檢查並安裝更新。

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. 編譯您的應用程式。

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 Mage.exe 部署以程式設計方式檢查更新的應用程式

- 請依照逐步解說[：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中所述的 Mage.exe，遵循部署應用程式的指示。 呼叫 Mage.exe 以產生部署資訊清單時，請務必使用命令列參數 `providerUrl` ，並指定 ClickOnce 應該檢查更新的 URL。 例如，如果您的應用程式將從更新 `http://www.adatum.com/MyApp` ，則您對產生部署資訊清單的呼叫可能如下所示：

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 MageUI.exe 部署以程式設計方式檢查更新的應用程式

- 請依照逐步解說[：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中所述的 Mage.exe，遵循部署應用程式的指示。 在 [**部署選項**] 索引標籤上，將 [**起始位置**] 欄位設定為應用程式資訊清單，ClickOnce 應該會檢查是否有更新。 在 [**更新選項**] 索引標籤上，清除 [**此應用程式應該檢查更新**] 核取方塊。

## <a name="net-framework-security"></a>.NET Framework 安全性
 您的應用程式必須具有完全信任許可權，才能使用以程式設計方式更新。

## <a name="see-also"></a>另請參閱
- [如何：指定部署更新的替代位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)