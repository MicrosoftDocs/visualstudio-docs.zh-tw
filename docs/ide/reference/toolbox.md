---
title: Visual Studio 中的工具箱視窗 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc7683e5796310eb35710c37fefe8cb861a83f48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="toolbox"></a>工具箱

[工具箱] 視窗顯示您可以加入 Visual Studio 專案的控制項。 若要開啟 [工具箱]，請選擇 [檢視] 功能表上的 [工具箱]。

![[工具箱] 視窗](media/toolbox.png)

您可以將不同的控制項拖放至所使用的設計工具介面上，並調整這些控制項的大小和位置。

工具箱會和設計工具檢視 (例如 XAML 檔的設計工具檢視) 一起顯示。 工具箱只會顯示可在目前的設計工具中使用的控制項。 您可以在 [工具箱] 內搜尋，以進一步篩選顯示的項目。

> [!NOTE]
> 對於某些專案類型，[工具箱] 可能不會顯示任何項目。

專案的目標 .NET Framework 版本也會影響 [工具箱] 中顯示的控制項集合。 您可以在專案的屬性頁，將專案的目標設定為其他的 .NET Framework 版本。 選取 [方案總管] 中的方案節點，然後在功能表列上選擇 [專案] > [\<專案\> 屬性]。 在 [應用程式] 索引標籤上，使用 [目標 Framework] 下拉式清單。

## <a name="managing-the-toolbox-window-and-its-controls"></a>管理工具箱視窗及其控制項

預設已在 Visual Studio IDE 左側摺疊 [工具箱]，將游標移至其上方就會顯示。 您可以釘選工具箱 (在其工具列上按一下**釘選**圖示)，使其在您移動游標時仍保持開啟狀態。 您也可以將工具箱視窗取消停駐，並拖曳至畫面上的任何位置。 您可以使用滑鼠右鍵按一下 [工具箱] 的工具列並選取其中一個選項，以將它停駐、取消停駐和隱藏。

您可以在操作功能表上使用下列命令，以重新排列 [工具箱] 索引標籤中的項目，或加入自訂索引標籤和項目：

- **重新命名項目** - 重新命名選取的項目。

- **全部顯示** - 顯示所有可能的控制項 (而不只是套用至目前設計工具的控制項)。

- **清單檢視** - 以垂直清單顯示控制項。 若未核取，則會以水平方式顯示控制項。

- **選擇項目** - 開啟 [選擇工具箱項目] 對話方塊，以供您指定在 [工具箱] 中顯示的項目。 您可以選取或清除某個項目的核取方塊，以顯示或隱藏該項目。

- **依字母順序排序項目** - 依名稱排序項目。

- **重設工具列** - 還原預設 [工具箱] 設定和項目。

- **新增索引標籤** - 新增 [工具箱] 索引標籤。

- **上移** - 向上移動選取的項目。

- **下移** - 向下移動選取的項目。

## <a name="creating-and-distributing-custom-toolbox-controls"></a>建立及發佈自訂 [工具箱] 控制項

您可以使用以 [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) 或 [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md) 為基礎的專案範本，以開始建立自訂 [工具箱] 控制項。 您接著可以將自訂控制項發佈給小組成員，或使用[工具箱控制項安裝程式](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)將它發佈到網路上。

## <a name="help-on-toolbox-tabs"></a>工具箱索引標籤上的說明

下列主題提供一些可用 [工具箱] 索引標籤的詳細資訊。

- [資料索引標籤、工具箱](../../ide/reference/toolbox-data-tab.md)

- [元件索引標籤、工具箱](../../ide/reference/toolbox-components-tab.md)

- [HTML 索引標籤、工具箱](../../ide/reference/toolbox-html-tab.md)
