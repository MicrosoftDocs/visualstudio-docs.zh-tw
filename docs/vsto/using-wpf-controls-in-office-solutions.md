---
title: 在 Office 方案中使用 WPF 控制項
description: 瞭解如何使用 Windows Presentation Foundation (WPF) 控制項來設計 Visual Studio 中的使用者介面。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7bc720e6218e4cbb76b14f356d190b738e31ede3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921907"
---
# <a name="use-wpf-controls-in-office-solutions"></a>在 Office 方案中使用 WPF 控制項

雖然 Visual Studio 中使用 Office 開發工具所建立的解決方案設計成直接使用 Windows Form 控制項，您也可以在解決方案中使用 WPF 控制項。 Windows Presentation Foundation (WPF) 是 Windows Form 設計使用者介面的替代方式。 WPF 使用稱為 Extensible Application Markup Language (XAML) 的標記語言，提供納入 UI、媒體和文件新技術。 如需詳細資訊，請參閱 [WPF 總覽](/dotnet/framework/wpf/introduction-to-wpf)。

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

任何可在 Office 方案中裝載 Windows Form 控制項的 UI 元素，也可以裝載 WPF 控制項。 它們包括下列元素：

- 文件層級自訂的文件和工作表。

- 文件層級自訂的執行窗格。

- VSTO 增益集的自訂工作窗格。

- Outlook VSTO 增益集的表單區域。

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>在設計階段將 WPF 控制項加入 Office 專案

您無法在 Office 方案的 UI 元素中直接加入 WPF 控制項。 相反地，請將 **使用者控制項 (WPF)** 專案加入至您的專案，並將其作為 WPF 控制項的設計介面。 然後，在專案的 UI 元素中加入 WPF 使用者控制項。

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>在執行窗格、自訂工作窗格或表單區域加入 WPF 控制項

1. 開啟要加入自訂工作窗格、執行窗格或表單區域的專案。

2. 將 **(WPF) 專案的使用者控制項** 新增至專案。

3. 在 [ **工具箱**] 中，將 wpf 控制項加入 wpf 使用者控制項設計介面。

     依預設，當 WPF 使用者控制項設計工具開啟時，[ **工具箱** ] 只會包含 wpf 控制項。

4. 建置專案。

5. 在專案中加入執行窗格、表單區域或自訂工作窗格：

    - 若為表單區域，請將 [ **Outlook 表單區域** ] 專案加入至專案。 如需詳細資訊，請參閱 [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。

    - 在 [動作] 窗格中，將 [執行 **窗格控制項]** 或 [ **使用者控制項** ] 專案加入至專案。 如需詳細資訊，請參閱 [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。

    - 針對自訂工作窗格，將 [ **使用者控制項** ] 專案加入至專案。 如需詳細資訊，請參閱 [如何：將自訂工作窗格加入至應用程式](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。

6. 從 [**工具箱**] 的 *專案名稱*[ **wpf 使用者控制項**] 索引標籤中，將 WPF 使用者控制項拖曳至 [執行] 窗格、表單區域或自訂工作窗格的設計工具。

     Visual Studio 會自動建立在 UI 元素上裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。

7. 請重建專案。

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>在文件層級專案的文件或工作表中加入 WPF 控制項

1. 開啟 Word 或 Excel 的文件層級專案。

2. 將 **(WPF) 專案的使用者控制項** 新增至專案。

3. 在 [ **工具箱**] 中，將 wpf 控制項加入 wpf 使用者控制項設計介面。

4. 建置專案。

5. 加入 **使用者控制項** 專案 (也就是 Windows Forms 的使用者控制項) 至專案。

6. 開啟 Windows Form 使用者控制項的設計工具。

7. 從 [工具箱] 的 *專案名稱*[ **wpf 使用者控制項** ] 索引標籤中，將 wpf 使用者控制項拖曳至設計 **工具**。

     Visual Studio 會自動建立在 Windows Form 使用者控制項中裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。

8. 撰寫程式碼，以程式設計方式將 Windows Form 使用者控制項加入文件或活頁簿。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

    > [!NOTE]
    > 您無法將 Windows Form 使用者控制項拖曳至設計工具的文件或工作表。

9. 請重建專案。

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>使用 ElementHost 類別裝載 WPF 控制項

Visual Studio 提供的功能，會協助您在 Office 方案中使用 Windows Form 控制項，但對 WPF 控制項則不提供類似的功能。 例如，您可以在設計階段從 [ **工具箱**] 拖曳控制項，或在執行時間使用 helper 方法，將 Windows Forms 控制項加入檔和工作表。 不過，WPF 控制項無法使用這些工具。

WPF 控制項將 <xref:System.Windows.Forms.Integration.ElementHost> 類別用做 Windows Form 控制項或表單和 WPF 控制項之間的整合層。 當您在設計階段將 WPF 控制項加入解決方案時，Visual Studio 會為您自動產生 <xref:System.Windows.Forms.Integration.ElementHost> 物件。

## <a name="wpf-resources"></a>WPF 資源

如需在 Windows Form 控制項和表單上裝載 WPF 控制項的架構和設計問題的詳細資訊，請參閱下列主題：

- [Windows Forms 和 WPF 互通性輸入架構](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Windows Forms 和 WPF 屬性對應](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [WPF 和 Windows Forms 交互操作](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Windows Forms 控制項和對等 WPF 控制項](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

如需在設計階段於 Visual Studio 的 Windows Form 控制項和表單中加入 WPF 控制項的詳細資訊，請參閱下列主題：

- [逐步解說：在設計階段于 Windows Forms 建立新的 WPF 內容](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [逐步解說：在設計階段將 WPF 內容排列 Windows Forms](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [逐步解說：樣式 WPF 內容](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>另請參閱

- [Office UI 自訂](../vsto/office-ui-customization.md)
- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [自訂工作窗格](../vsto/custom-task-panes.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [如何：將自訂工作窗格加入至應用程式](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
