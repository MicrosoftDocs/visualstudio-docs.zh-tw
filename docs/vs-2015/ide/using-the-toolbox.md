---
title: 使用工具箱 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba8a37ac9e049455ffe19314dee0e228c3c14c97
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295611"
---
# <a name="using-the-toolbox"></a>使用工具箱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用工具箱將控制項和其他項目加入至專案。 您可以將不同的控制項拖放至所使用的設計工具介面上，並調整這些控制項的大小和位置。

 工具箱會和設計工具檢視 (例如 XAML 檔的設計工具檢視) 一起顯示。 工具箱只會顯示可在目前的設計工具中使用的控制項。

 專案的目標 .NET Framework 版本也會影響工具箱中顯示的控制項集合。 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 專案預設會以 .NET Framework 4.5.1 為目標。 您可以在方案總管中選取專案節點，然後瀏覽至 [屬性/應用程式/目標 Framework]，將專案的目標設定為不同版本的 .NET Framework。

## <a name="managing-the-toolbox-and-its-controls"></a>管理工具箱及其控制項
 預設已在 Visual Studio IDE 左側摺疊工具箱，您可以將游標移至上方加以顯示。 您可以釘選工具箱 (在工具箱工具列上按一下釘選圖示)，使其在移動游標時仍保持開啟狀態。 您也可以取消停駐工具箱視窗，並將其拖曳至畫面上的任何位置。 您可以使用滑鼠右鍵按一下工具箱工具列並選取其中一個選項，以停駐、取消停駐和隱藏工具箱。

 您可以在操作功能表上使用下列命令重新排列工具箱索引標籤中的項目，或加入自訂索引標籤和項目：

- **重新命名項目** - 重新命名選取的項目。

- **全部顯示** - 顯示所有可能的控制項 (而不只是套用至目前設計工具的控制項)。

- **清單檢視** - 以垂直清單顯示控制項。 若未核取，則會以水平方式顯示控制項。

- **選擇項目** - 開啟 [選擇工具箱項目] 對話方塊，以供您指定在 [工具箱] 中顯示的項目。 您可以選取或清除某個項目的核取方塊，以顯示或隱藏該項目。

- **依字母順序排序項目** - 依名稱排序項目。

- **重設工具列** - 還原預設的工具箱設定和項目。

- **加入索引標籤** - 加入新的工具箱索引標籤。

- **上移** - 向上移動選取的項目。

- **下移** - 向下移動選取的項目。

## <a name="creating-and-distributing-custom-toolbox-controls"></a>建立及發佈自訂工具箱控制項
 您可以在 Visual Basic 或 Visual C# 中建立自訂工具箱控制項，也可以使用以 [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) 或 [Windows Form](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) 為基礎的專案範本開始作業。 您接著可以將控制項發佈給小組成員，或使用 [工具箱控制項安裝程式](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)將它發佈到網站。
