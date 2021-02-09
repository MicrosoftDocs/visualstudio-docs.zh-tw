---
title: 擴充 Visual Studio 中的 SharePoint 工具 |Microsoft Docs
description: 在 Visual Studio 中擴充 SharePoint 工具。 擴充 SharePoint 專案系統。 擴充伺服器總管中的 [SharePoint 連接] 節點。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c074e62b47b926351948e94d78621a8a41c9c3e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876845"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>擴充 Visual Studio 中的 SharePoint 工具
  Visual Studio 中的 SharePoint 工具符合許多應用程式開發案例的需求。 不過，您可能會發現它們並未提供您或其他開發人員所需的功能。 在這些情況下，您可以擴充 SharePoint 工具來建立您所需的功能。

## <a name="how-to-extend-the-sharepoint-tools"></a>如何擴充 SharePoint 工具
 您可以在 [**伺服器總管**] 視窗中，擴充 sharepoint 專案系統和 [ **sharepoint 連接**] 節點。

### <a name="extend-the-sharepoint-project-system"></a>擴充 SharePoint 專案系統
 Visual Studio 包含一組可供您用來建立 SharePoint 方案的專案範本和專案範本。 例如，有適用于事件接收器、清單定義、工作流程和 Web 組件的範本。 不過，您也可以定義自己的 SharePoint 專案專案類型，以建立 SharePoint 元件，例如欄位或自訂動作。 您也可以建立已安裝在 Visual Studio 中的 SharePoint 專案專案類型的延伸模組，也可以建立 SharePoint 專案的擴充功能。

 如需詳細資訊，請參閱 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>擴充伺服器總管中的 [SharePoint 連接] 節點
 在 Visual Studio 中，您可以使用 [**伺服器總管**] 視窗中的 [ **SharePoint 連接**] 節點，以階層式樹狀檢視來查看一或多個本機 SharePoint 網站的許多元件。 您也可以利用下列方式來擴充 [ **SharePoint 連接** ] 節點：

- 藉由新增您自己的節點。 如果您想要顯示預設不會顯示的 SharePoint 網站元件，這會很有用。

- 藉由擴充現有的節點。 例如，您可以將新的子節點加入至現有的節點，也可以將快捷方式功能表項目加入至節點，並在開發人員按一下功能表項目時執行工作。

  如需詳細資訊，請參閱 [伺服器總管中的擴充 SharePoint 連接節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

## <a name="development-computer-requirements"></a>開發電腦需求
 若要建立 SharePoint 工具的擴充功能，您的開發電腦必須符合在 Visual Studio 中建立 SharePoint 方案的相同需求。

 我們也建議您安裝 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] 。 SDK 包含可供您用來擴充 Visual Studio 的專案範本和工具。 特別是，SDK 包含專案範本，可讓您輕鬆地建立 Visual Studio 擴充功能 (VSIX) 套件。 VSIX 封裝是在 Visual Studio 中部署 Visual Studio 擴充功能的慣用方法。 所有的 SharePoint 工具延伸模組都必須使用 VSIX 套件來部署。 本檔中的所有逐步解說都假設您已 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] 安裝。

 若要安裝 Visual Studio SDK，請參閱 [安裝 VISUAL STUDIO sdk](../extensibility/installing-the-visual-studio-sdk.md)。 如需 Visual Studio 擴充功能的詳細資訊，請參閱 [開始開發 Visual Studio 擴充](../extensibility/starting-to-develop-visual-studio-extensions.md)功能。

## <a name="see-also"></a>另請參閱

- [SharePoint 工具擴充功能的程式設計模型總覽](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [擴充伺服器總管中的 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 工具擴充功能的程式設計概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [&#40;SharePoint 工具擴充性的參考&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio 中 SharePoint 工具的 Debug 擴充功能](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [在 Visual Studio 中部署 SharePoint 工具的延伸模組](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)