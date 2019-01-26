---
title: 在 Office 方案中使用 WPF 控制項
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 70c77e3b093947703680ab7253fdee0a6c3d60cd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869758"
---
# <a name="use-wpf-controls-in-office-solutions"></a>在 Office 方案中使用 WPF 控制項

雖然 Visual Studio 中使用 Office 開發工具所建立的解決方案設計成直接使用 Windows Form 控制項，您也可以在解決方案中使用 WPF 控制項。 Windows Presentation Foundation (WPF) 是 Windows Form 設計使用者介面的替代方式。 WPF 使用稱為 Extensible Application Markup Language (XAML) 的標記語言，提供納入 UI、媒體和文件新技術。 如需詳細資訊，請參閱 < [WPF 概觀](../designers/introduction-to-wpf.md)。

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

任何可在 Office 方案中裝載 Windows Form 控制項的 UI 元素，也可以裝載 WPF 控制項。 它們包括下列元素：

-   文件層級自訂的文件和工作表。

-   文件層級自訂的執行窗格。

-   VSTO 增益集的自訂工作窗格。

-   Outlook VSTO 增益集的表單區域。

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>在設計階段將 WPF 控制項加入 Office 專案

您無法在 Office 方案的 UI 元素中直接加入 WPF 控制項。 相反地，新增**使用者控制項 (WPF)** 至您的專案項目，然後作為 WPF 控制項的設計介面。 然後，在專案的 UI 元素中加入 WPF 使用者控制項。

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>在執行窗格、自訂工作窗格或表單區域加入 WPF 控制項

1.  開啟要加入自訂工作窗格、執行窗格或表單區域的專案。

2.  新增**使用者控制項 (WPF)** 項目加入您的專案。

3.  從**工具箱**，將 WPF 控制項加入 WPF 使用者控制項的設計介面。

     根據預設，當 WPF 使用者控制項設計工具開啟時，**工具箱**只包含 WPF 控制項。

4.  建置專案。

5.  在專案中加入執行窗格、表單區域或自訂工作窗格：

    -   針對表單區域，新增**Outlook 表單區域**項目加入專案。 如需詳細資訊，請參閱[＜How to：將表單區域加入 Outlook 增益集專案](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。

    -   針對 [動作] 窗格中，新增**執行窗格控制項**或是**使用者控制**項目加入專案。 如需詳細資訊，請參閱[＜How to：加入執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)和[How to:加入執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。

    -   對於自訂工作窗格，請新增**使用者控制項**項目加入專案。 如需詳細資訊，請參閱[＜How to：應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。

6.  從*ProjectName* **WPF 使用者控制項**索引標籤**工具箱**，將 WPF 使用者控制項拖曳至 [動作] 窗格、 表單區域或自訂工作窗格的設計工具。

     Visual Studio 會自動建立在 UI 元素上裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。

7.  重建專案。

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>在文件層級專案的文件或工作表中加入 WPF 控制項

1.  開啟 Word 或 Excel 的文件層級專案。

2.  新增**使用者控制項 (WPF)** 項目加入您的專案。

3.  從**工具箱**，將 WPF 控制項加入 WPF 使用者控制項的設計介面。

4.  建置專案。

5.  新增**使用者控制項**至專案的項目 （也就是 Windows Form 使用者控制項）。

6.  開啟 Windows Form 使用者控制項的設計工具。

7.  從*ProjectName* **WPF 使用者控制項**索引標籤**工具箱**，將 WPF 使用者控制項拖曳至設計工具。

     Visual Studio 會自動建立在 Windows Form 使用者控制項中裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。

8.  撰寫程式碼，以程式設計方式將 Windows Form 使用者控制項加入文件或活頁簿。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。

    > [!NOTE]
    > 您無法將 Windows Form 使用者控制項拖曳至設計工具的文件或工作表。

9. 重建專案。

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>將 WPF 控制項裝載使用 ElementHost 類別

Visual Studio 提供的功能，會協助您在 Office 方案中使用 Windows Form 控制項，但對 WPF 控制項則不提供類似的功能。 比方說，您可以將 Windows Form 控制項加入文件和工作表在設計階段拖曳控制項從**工具箱**，或在執行階段使用 helper 方法。 不過，WPF 控制項無法使用這些工具。

WPF 控制項將 <xref:System.Windows.Forms.Integration.ElementHost> 類別用做 Windows Form 控制項或表單和 WPF 控制項之間的整合層。 當您在設計階段將 WPF 控制項加入解決方案時，Visual Studio 會為您自動產生 <xref:System.Windows.Forms.Integration.ElementHost> 物件。

## <a name="wpf-resources"></a>WPF 資源

如需在 Windows Form 控制項和表單上裝載 WPF 控制項的架構和設計問題的詳細資訊，請參閱下列主題：

-   [Windows Form 和 WPF 互通性輸入的架構](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

-   [Windows Form 和 WPF 屬性對應](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

-   [WPF 和 Windows Forms 互通性](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

-   [Windows Forms 控制項和對等 WPF 控制項](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

如需在設計階段於 Visual Studio 的 Windows Form 控制項和表單中加入 WPF 控制項的詳細資訊，請參閱下列主題：

-   [逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

-   [逐步解說：在設計階段排列 Windows Form 的 WPF 內容](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

-   [逐步解說：樣式的 WPF 內容](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>另請參閱

- [Office UI 自訂](../vsto/office-ui-customization.md)
- [在 Office 文件概觀上的 Windows Form 控制項](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [執行窗格概觀](../vsto/actions-pane-overview.md)
- [自訂工作窗格](../vsto/custom-task-panes.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [如何：執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [如何：應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [如何：將表單區域加入 Outlook 增益集專案](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
