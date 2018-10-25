---
title: 擴充 Visual Studio 中的 SharePoint 工具 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f360982f26cf2eb9ffe26678743bb514d9606ae7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890669"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>擴充 Visual Studio 中的 SharePoint 工具
  Visual Studio 中的 SharePoint 工具符合許多應用程式開發案例的需求。 不過，您可能會發現情況下，它們並不提供您或其他開發人員需要的功能。 在這些情況下，您可以擴充 SharePoint 工具來建立您所需要的功能。

## <a name="how-to-extend-the-sharepoint-tools"></a>如何擴充 SharePoint 工具
 您可以擴充 SharePoint 專案系統和**SharePoint 連線**中的節點**伺服器總管**視窗。

### <a name="extend-the-sharepoint-project-system"></a>擴充 SharePoint 專案系統
 Visual Studio 包含一組專案範本和項目範本可供您建立 SharePoint 方案。 比方說，有事件接收器、 清單定義、 工作流程和 Web 組件範本。 不過，您也可以定義您自己的 SharePoint 專案項目，用於建立 SharePoint 的元件，例如欄位或自訂動作的類型。 您也可以建立已安裝在 Visual Studio 中的 SharePoint 專案項目類型的延伸模組，而且您可以建立 SharePoint 專案延伸模組。

 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>擴充 SharePoint 連線節點，在 伺服器總管
 在 Visual Studio 中，您可以使用**SharePoint 連線**中的節點**伺服器總管**視窗來檢視在階層樹狀結構檢視中的許多元件的其中一個或多個本機 SharePoint 網站。 您也可以擴充**SharePoint 連線**節點，以下列方式：

- 藉由新增您自己的節點。 這非常有用，如果您想要顯示的預設未顯示的 SharePoint 網站的元件。

- 藉由擴充現有的節點。 例如，您可以將新的子節點加入現有的節點，或您可以將加入節點的捷徑功能表項目，並為開發人員按一下功能表項目時所執行的工作。

  如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

## <a name="development-computer-requirements"></a>開發電腦的需求
 若要建立 SharePoint 工具擴充功能，您的開發電腦必須符合在 Visual Studio 中建立 SharePoint 方案的相同需求。

 我們也建議您安裝[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 SDK 包含專案範本和工具，您可以用來擴充 Visual Studio。 特別是，SDK 包含專案範本可用來輕鬆地建立 Visual Studio 擴充功能 (VSIX) 封裝。 VSIX 套件是部署在 Visual Studio 中的 Visual Studio 擴充功能的慣用的方式。 使用 VSIX 封裝，必須部署所有的 SharePoint 工具擴充功能。 所有的這份文件中的逐步解說假設您有[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]安裝。

 若要安裝 Visual Studio SDK，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。 如需有關 Visual Studio 擴充功能的詳細資訊，請參閱 <<c0> [ 開始開發 Visual Studio 擴充功能](../extensibility/starting-to-develop-visual-studio-extensions.md)。

## <a name="see-also"></a>另請參閱

- [概觀的程式設計模型的 SharePoint 工具擴充功能](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 工具擴充功能的程式設計概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [參考&#40;SharePoint 工具擴充性&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [偵錯在 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)