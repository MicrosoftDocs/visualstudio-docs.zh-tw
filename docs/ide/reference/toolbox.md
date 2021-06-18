---
title: '[工具箱] 視窗'
description: 瞭解 [工具箱] 視窗，以及它如何顯示您可以新增至 Visual Studio 專案的控制項。
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a926084ccd8b1aafabb50f5a93f3f46d77bc6d4
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308463"
---
# <a name="toolbox"></a>工具箱

[工具箱] 視窗顯示您可以加入 Visual Studio 專案的控制項。 若要開啟 [**工具箱**]，請從功能表列選擇 [ **View**  >  **工具箱**]，或按 **Ctrl** + **Alt** + **X**。

![[工具箱] 視窗的螢幕擷取畫面，其中顯示 [容器] 區段中的選項。](media/vs-2019/toolbox.png "[工具箱] 視窗的螢幕擷取畫面")

您可以將不同的控制項拖放至所使用的設計工具介面上，並調整這些控制項的大小和位置。

[工具箱] 會與設計師視圖一起出現，例如 XAML 檔案的設計工具或 Windows Forms 應用程式專案。 [工具箱] 只會顯示可在目前的設計工具中使用的控制項。 您可以在 [工具箱] 內搜尋，以進一步篩選顯示的項目。

> [!NOTE]
> 針對某些專案類型，[工具箱] 可能不會顯示任何項目。

專案的目標 .NET 版本也會影響 [工具箱] 中顯示的控制項集合。 如有必要，您可以從專案的屬性頁變更目標 Framework 版本。 選取 [方案總管] 中的方案節點，然後在功能表列上選擇 [專案] > [projectname 屬性]。 在 [應用程式] 索引標籤上，使用 [目標 Framework] 下拉式清單。

::: moniker range=">=vs-2019"

![[應用程式] 對話方塊的螢幕擷取畫面，其中顯示 [目標 framework] 下拉式清單中的選項。](media/vs-2019/toolbox-change-dotnet-version.png "對話方塊的螢幕擷取畫面，您可以在其中變更 .NET 版本")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>管理工具箱視窗及其控制項

依預設，[ **工具箱** ] 會沿著 Visual Studio IDE 的左邊折迭，並在游標移至其上方時顯示。 您可以釘選 [工具箱] (在其工具列上按一下 [釘選] 圖示)，使其在您移動游標時仍保持開啟狀態。 您也可以將 [工具箱] 視窗取消停駐，並拖曳至畫面上的任何位置。 您可以使用滑鼠右鍵按一下 [工具箱] 的工具列並選取其中一個選項，以將它停駐、取消停駐和隱藏。

> [!TIP]
> 如果工具箱在 Visual Studio IDE 的左邊不會再顯示為折迭，您可以從功能表列選擇 [**視窗**  >  **重設視窗** 配置]，將它重新加入。

您可以使用滑鼠右鍵內容功能表上的下列命令，重新排列 [ **工具箱** ] 索引標籤中的專案，或加入自訂索引標籤和專案：

- **重新命名專案-重新** 命名選取的專案。

- **清單檢視** - 以垂直清單顯示控制項。 若未核取，則會以水平方式顯示控制項。

- **全部顯示** - 顯示所有可能的控制項 (而不只是套用至目前設計工具的控制項)。

- **選擇項目** - 開啟 [選擇工具箱項目] 對話方塊，以供您指定在 [工具箱] 中顯示的項目。 您可以選取或清除某個項目的核取方塊，以顯示或隱藏該項目。

- 依 **字母順序排序專案**-依名稱排序專案。

- **重設工具列** - 還原預設 [工具箱] 設定和項目。

- **新增索引標籤** - 新增 [工具箱] 索引標籤。

- **上移** - 向上移動選取的項目。

- **下移** - 向下移動選取的項目。

## <a name="create-and-distribute-custom-toolbox-controls"></a>建立和散發自訂工具箱控制項

您可以使用以 [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) 或 [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md) 為基礎的專案範本，以開始建立自訂 [工具箱] 控制項。 您接著可以將自訂控制項發佈給小組成員，或使用[工具箱控制項安裝程式](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)將它發佈到網路上。

## <a name="next-steps"></a>後續步驟

詳閱下列連結，以深入瞭解一些可用的 [ **工具箱** ] 索引標籤：

- [工具箱, 資料索引標籤](../../ide/reference/toolbox-data-tab.md)
- [元件索引標籤、工具箱](../../ide/reference/toolbox-components-tab.md)
- [HTML 索引標籤、工具箱](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>另請參閱

- [選擇工具箱項目、WPF 元件](choose-toolbox-items-wpf-components.md)
