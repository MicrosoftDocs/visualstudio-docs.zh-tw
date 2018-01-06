---
title: "呼叫 SharePoint 物件模型 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b1a0f4175dc884283dcf92b7f6268a518cdaf0ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="calling-into-the-sharepoint-object-models"></a>呼叫 SharePoint 物件模型
  當您在 Visual Studio 中建立 SharePoint 工具擴充功能時，您可能需要呼叫 SharePoint Api 來執行特定工作。 比方說，如果您建立 SharePoint 專案的自訂部署步驟，您可能需要呼叫 SharePoint Api 來執行一些工作來部署解決方案。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]提供您可以使用 SharePoint 工具擴充功能中的兩個不同的物件模型： 伺服器物件模型和用戶端物件模型。 每個物件模型中的 SharePoint 工具擴充功能的內容中有優點和缺點。  
  
 如需 SharePoint 物件模型的概觀，請參閱[程式設計模型的 SharePoint 工具擴充功能的概觀](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>在擴充功能專案中使用用戶端物件模型  
 當您開發 SharePoint 工具擴充功能時，您可以像任何其他的受管理的 Api 集專案中使用用戶端物件模型。 用戶端物件模型中將組件的參考加入至您的專案，您可以在用戶端物件模型呼叫應用程式開發介面，直接從程式碼。  
  
 不過，用戶端物件模型在 SharePoint 工具擴充功能的內容中有這兩個缺點：  
  
-   用戶端物件模型提供的伺服器物件模型的子集。 如果您有使用不會出現在用戶端物件模型的 SharePoint 功能，您必須使用伺服器物件模型。  
  
-   雖然用戶端物件模型中 SharePoint 工具擴充功能應該使用在大部分情況下，您可能會遇到某些案例中，用戶端物件模型呼叫執行無法如預期運作。 用戶端物件模型被設計用於用戶端應用程式來呼叫遠端伺服器或伺服陣列上的 SharePoint 網站。 Visual Studio 中的 SharePoint 工具僅適用於開發電腦上的本機 SharePoint 安裝。 因此，當您使用用戶端物件模型中的 SharePoint 工具擴充功能，您呼叫 SharePoint 網站的本機電腦上，也就是沒有用戶端物件模型的設計方式使用。  
  
 如需示範如何使用用戶端物件模型中的 Visual Studio 中的 SharePoint 工具擴充功能的逐步解說，請參閱[逐步解說： 呼叫 SharePoint 用戶端物件模型，在伺服器總管擴充功能](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>在擴充功能專案中使用伺服器物件模型  
 伺服器物件模型是用戶端物件模型的超集。 當您使用伺服器物件模型時，您可以使用所有功能，[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]以程式設計方式公開。  
  
 SharePoint 工具擴充功能可以使用伺服器物件模型中的 Api，但他們不能直接呼叫 Api。 目標為.NET Framework 3.5 時，伺服器物件模型可以是只從 64 位元處理序呼叫。 不過，SharePoint 工具擴充功能需要[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]和其在 32 位元 Visual Studio 處理序中執行。 這可防止直接參考的組件在 SharePoint 伺服器物件模型中 SharePoint 工具擴充功能。  
  
 如果您想要使用伺服器物件模型中的 SharePoint 工具擴充功能，您必須建立自訂*SharePoint 命令*來呼叫 API。 您可以直接呼叫伺服器物件模型的第二個組件中定義 SharePoint 命令。 在擴充功能專案中，您呼叫 SharePoint 命令間接使用 ExecuteCommand 方法<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>物件。  
  
 如需有關建立及使用 SharePoint 命令的詳細資訊，請參閱[How to： 建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)和[如何： 執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。 如需如何部署 SharePoint 命令的資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
 如需示範如何建立及使用 SharePoint 命令的逐步解說，請參閱[逐步解說： 建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)和[逐步解說： 擴充伺服器總管 來顯示網頁組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
### <a name="understanding-how-sharepoint-commands-are-executed"></a>了解如何 SharePoint 命令會執行  
 定義 SharePoint 命令的組件會在名為 vssphost4.exe 64 位元主控件程序中載入的。 中的 SharePoint 工具擴充功能呼叫 SharePoint 命令之後，而不是 32 位元 Visual Studio 處理序 (devenv.exe) vssphost4.exe 執行命令。 您可以控制如何在登錄中設定值執行 SharePoint 命令的某些層面。 如需詳細資訊，請參閱[偵錯 Visual Studio 中 SharePoint 工具的延伸模組](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [如何： 執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [SharePoint 工具延伸模組的程式撰寫模型概觀](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  