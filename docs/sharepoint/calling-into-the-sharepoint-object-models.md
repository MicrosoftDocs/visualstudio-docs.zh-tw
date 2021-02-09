---
title: 呼叫 SharePoint 物件模型 |Microsoft Docs
description: 瞭解如何呼叫您可以在 SharePoint 工具擴充功能中使用的兩個不同物件模型。
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14358b5cc84f63227fd5001731c261002a324492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928935"
---
# <a name="call-into-the-sharepoint-object-models"></a>呼叫 SharePoint 物件模型
  當您在 Visual Studio 中建立 SharePoint 工具的延伸模組時，您可能必須呼叫 SharePoint Api 來執行某些工作。 例如，如果您建立 SharePoint 專案的自訂部署步驟，您可能必須呼叫 SharePoint Api 來執行一些工作，以部署方案。

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 提供兩種不同的物件模型，可讓您在 SharePoint 工具擴充功能中使用：伺服器物件模型和用戶端物件模型。 每個物件模型在 SharePoint 工具延伸模組的內容中都有其優點和缺點。

 如需 SharePoint 物件模型的總覽，請參閱 [sharepoint 工具擴充功能的程式設計模型總覽](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。

## <a name="use-the-client-object-model-in-extension-projects"></a>在擴充功能專案中使用用戶端物件模型
 當您開發 SharePoint 工具的延伸模組時，您可以在專案中使用用戶端物件模型，就像任何其他受控 Api 集一樣。 您可以將用戶端物件模型中的元件參考加入至專案，也可以直接從程式碼呼叫用戶端物件模型中的 Api。

 不過，在 SharePoint 工具擴充功能的環境中，用戶端物件模型有兩個缺點：

- 用戶端物件模型只會提供伺服器物件模型的子集。 如果您必須使用未在用戶端物件模型中公開的 SharePoint 功能，則必須使用伺服器物件模型。

- 雖然在大部分情況下使用 [SharePoint 工具延伸模組] 中的用戶端物件模型，但您可能會遇到某些情況下，用戶端物件模型的呼叫無法如預期般運作。 用戶端物件模型的設計目的是要用於用戶端應用程式，以呼叫遠端伺服器或伺服器陣列上的 SharePoint 網站。 Visual Studio 中的 SharePoint 工具只適用于開發電腦上的本機 SharePoint 安裝。 因此，當您在 SharePoint 工具擴充功能中使用用戶端物件模型時，您會呼叫本機電腦上的 SharePoint 網站，而不是使用設計用戶端物件模型的方式。

  如需示範如何在 Visual Studio 的 SharePoint 工具擴充功能中使用用戶端物件模型的逐步解說，請參閱 [逐步解說：在伺服器總管擴充功能中呼叫 sharepoint 用戶端物件模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。

## <a name="use-the-server-object-model-in-extension-projects"></a>在擴充功能專案中使用伺服器物件模型
 伺服器物件模型是用戶端物件模型的超集合。 當您使用伺服器物件模型時，您可以使用和以程式設計 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 方式公開的所有功能 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 。

 SharePoint 工具擴充功能可以使用伺服器物件模型中的 Api，但無法直接呼叫 Api。 伺服器物件模型只能從以 .NET Framework 3.5 為目標的64位進程中呼叫。 不過，SharePoint 工具延伸模組需要， [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 而且它們會在32位 Visual Studio 進程中執行。 這可防止 SharePoint 工具延伸模組直接參考 SharePoint server 物件模型中的元件。

 如果您想要在 SharePoint 工具擴充功能中使用伺服器物件模型，您必須建立自訂 *SharePoint 命令* 以呼叫 API。 您可以在可以直接呼叫伺服器物件模型的次要元件中定義 SharePoint 命令。 在擴充功能專案中，您可以使用物件的 ExecuteCommand 方法，間接呼叫 SharePoint 命令 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 。

 如需建立和使用 SharePoint 命令的詳細資訊，請參閱 [如何：建立 sharepoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md) 和 how [To：執行 sharepoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。 如需如何部署 SharePoint 命令的詳細資訊，請參閱 [Visual Studio 中的部署 sharepoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

 如需示範如何建立和使用 SharePoint 命令的逐步解說，請參閱 [逐步解說：建立 sharepoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) 和 [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。

### <a name="understand-how-sharepoint-commands-are-executed"></a>瞭解如何執行 SharePoint 命令
 定義 SharePoint 命令的元件會載入名為 *vssphost4.exe* 的64位主機進程中。 當您在 SharePoint 工具擴充功能中呼叫 SharePoint 命令之後，命令會由 *vssphost4.exe* 執行，而不是32位 Visual Studio 進程 (*devenv.exe*) 。 您可以藉由設定登錄中的值，來控制如何執行 SharePoint 命令的某些層面。 如需詳細資訊，請參閱 [Visual Studio 中 SharePoint 工具的 Debug 擴充](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [如何：建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)
- [How to：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [SharePoint 工具擴充功能的程式設計模型總覽](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
