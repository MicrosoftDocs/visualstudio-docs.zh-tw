---
title: 呼叫 SharePoint 物件模型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: df55347ea08bfcb243f37aaee111066106da49ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914523"
---
# <a name="call-into-the-sharepoint-object-models"></a>呼叫 SharePoint 物件模型
  當您在 Visual Studio 中建立 SharePoint 工具擴充功能時，您可能必須呼叫 SharePoint Api 來執行特定工作。 例如，如果您建立 SharePoint 專案的自訂部署步驟時，您可能在呼叫 SharePoint Api 來執行一些工作，以部署解決方案。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]提供您可以使用 SharePoint 工具擴充功能中的兩個不同的物件模型： 伺服器物件模型和用戶端物件模型。 每個物件模型有優點和缺點 SharePoint 工具擴充功能的內容中。  
  
 如需 SharePoint 物件模型的概觀，請參閱 <<c0> [ 概觀的程式設計模型的 SharePoint 工具擴充功能](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## <a name="use-the-client-object-model-in-extension-projects"></a>在擴充功能專案中使用用戶端物件模型
 當您開發 SharePoint 工具擴充功能時，您就可以像任何其他的受管理的 Api 集專案中使用用戶端物件模型。 在用戶端物件模型中將組件的參考新增至您的專案，您可以在用戶端物件模型呼叫 Api，直接從程式碼。  
  
 不過，用戶端物件模型會在 SharePoint 工具擴充功能的內容中，有兩個缺點：  
  
- 用戶端物件模型會提供只有伺服器物件模型的子集。 如果您有使用中用戶端物件模型未公開的 SharePoint 功能，您必須使用伺服器物件模型。  
  
- 雖然使用用戶端物件模型中 SharePoint 工具擴充功能應該適用於大部分的情況下，您可能會遇到某些情況下，呼叫用戶端物件模型執行未如預期般運作。 用戶端物件模型可用於呼叫 SharePoint 網站上的遠端伺服器或伺服陣列用戶端應用程式。 Visual Studio 中 SharePoint 工具只使用本機 SharePoint 安裝在開發電腦上。 因此，當您使用用戶端物件模型中 SharePoint 工具擴充功能時，您呼叫 SharePoint 網站的本機電腦上，也就是沒有用戶端物件模型的設計方式使用。  
  
  如需示範如何使用用戶端物件模型中的 Visual Studio 中 SharePoint 工具延伸模組的逐步解說，請參閱[逐步解說：呼叫 SharePoint 用戶端物件模型，在 伺服器總管延伸模組](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## <a name="use-the-server-object-model-in-extension-projects"></a>在擴充功能專案中使用伺服器物件模型
 伺服器物件模型是用戶端物件模型的超集。 當您使用伺服器物件模型時，您可以使用所有功能，[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]以程式設計方式公開。  

 SharePoint 工具擴充功能可以在伺服器物件模型中，使用 Api，但他們不能直接呼叫 Api。 .NET Framework 3.5 為目標時，伺服器物件模型可以是只從 64 位元處理序呼叫。 不過，SharePoint 工具擴充功能需要[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]和其在 32 位元 Visual Studio 處理序中執行。 這可防止直接參考的組件在 SharePoint 伺服器物件模型中 SharePoint 工具擴充功能。  
  
 如果您想要使用 SharePoint 工具擴充功能中的伺服器物件模型，您必須建立自訂*SharePoint 命令*來呼叫 API。 您可以直接呼叫伺服器物件模型的第二個組件中定義之 SharePoint 命令。 在擴充功能專案中，您的 SharePoint 命令間接使用呼叫的 ExecuteCommand 方法<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>物件。  
  
 如需有關建立和使用 SharePoint 命令的詳細資訊，請參閱[How to:建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)和[How to:執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。 如需如何部署 SharePoint 命令的詳細資訊，請參閱[部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
 如需示範如何建立和使用 SharePoint 命令的逐步解說，請參閱[逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)和[逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>了解如何執行 SharePoint 命令
 定義 SharePoint 命令的組件會在名為 64 位元主機處理序中載入*vssphost4.exe*。 您在 SharePoint 工具擴充功能呼叫 SharePoint 命令之後，執行命令*vssphost4.exe*而不是 32 位元 Visual Studio 處理序 (*devenv.exe*)。 您可以控制如何執行 SharePoint 命令的設定值，在登錄中的某些層面。 如需詳細資訊，請參閱 <<c0> [ 偵錯在 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [如何：建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [如何：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [概觀的程式設計模型的 SharePoint 工具擴充功能](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
