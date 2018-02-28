---
title: "在 Office 方案中使用 WPF 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 74ee8c574f6f654aca166844d85a30f2d3d9d4c3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="using-wpf-controls-in-office-solutions"></a>在 Office 方案中使用 WPF 控制項
  雖然 Visual Studio 中使用 Office 開發工具所建立的解決方案設計成直接使用 Windows Form 控制項，您也可以在解決方案中使用 WPF 控制項。 Windows Presentation Foundation (WPF) 是 Windows Form 設計使用者介面的替代方式。 WPF 使用稱為 Extensible Application Markup Language (XAML) 的標記語言，提供納入 UI、媒體和文件新技術。 如需詳細資訊，請參閱[Visual Studio 2015 中的 WPF 簡介](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 任何可在 Office 方案中裝載 Windows Form 控制項的 UI 元素，也可以裝載 WPF 控制項。 它們包括下列元素：  
  
-   文件層級自訂的文件和工作表。  
  
-   文件層級自訂的執行窗格。  
  
-   VSTO 增益集的自訂工作窗格。  
  
-   Outlook VSTO 增益集的表單區域。  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>在設計階段將 WPF 控制項加入 Office 專案中  
 您無法在 Office 方案的 UI 元素中直接加入 WPF 控制項。 請改為加入**使用者控制項 (WPF)**項目加入您的專案，並使用它的設計介面做為 WPF 控制項。 然後，在專案的 UI 元素中加入 WPF 使用者控制項。  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>在執行窗格、自訂工作窗格或表單區域加入 WPF 控制項  
  
1.  開啟要加入自訂工作窗格、執行窗格或表單區域的專案。  
  
2.  新增**使用者控制項 (WPF)**至您的專案項目。  
  
3.  從**工具箱**，將 WPF 控制項加入 WPF 使用者控制項的設計介面。  
  
     根據預設，WPF 使用者控制項設計工具開啟時，**工具箱**只包含 WPF 控制項。  
  
4.  建置專案。  
  
5.  在專案中加入執行窗格、表單區域或自訂工作窗格：  
  
    -   表單區域，新增**Outlook 表單區域**項目加入專案。 如需詳細資訊，請參閱[How to： 在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
    -   對於執行窗格加入**執行窗格控制項**或**使用者控制項**項目加入專案。 如需詳細資訊，請參閱[如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)和[如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
    -   對於自訂工作窗格，請新增**使用者控制項**項目加入專案。 如需詳細資訊，請參閱[How to： 應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。  
  
6.  從*ProjectName* **WPF 使用者控制項** 索引標籤**工具箱**，將 WPF 使用者控制項拖曳至 動作 窗格、 表單區域或自訂工作窗格的設計工具。  
  
     Visual Studio 會自動建立在 UI 元素上裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
7.  重建專案。  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>在文件層級專案的文件或工作表中加入 WPF 控制項  
  
1.  開啟 Word 或 Excel 的文件層級專案。  
  
2.  新增**使用者控制項 (WPF)**至您的專案項目。  
  
3.  從**工具箱**，將 WPF 控制項加入 WPF 使用者控制項的設計介面。  
  
4.  建置專案。  
  
5.  新增**使用者控制項**項目 （也就是 Windows Form 使用者控制項） 加入專案。  
  
6.  開啟 Windows Form 使用者控制項的設計工具。  
  
7.  從*ProjectName* **WPF 使用者控制項** 索引標籤**工具箱**，將 WPF 使用者控制項拖曳至設計工具。  
  
     Visual Studio 會自動建立在 Windows Form 使用者控制項中裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
8.  撰寫程式碼，以程式設計方式將 Windows Form 使用者控制項加入文件或活頁簿。 如需詳細資訊，請參閱 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
    > [!NOTE]  
    >  您無法將 Windows Form 使用者控制項拖曳至設計工具的文件或工作表。  
  
9. 重建專案。  
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>使用 ElementHost 類別裝載 WPF 控制項  
 Visual Studio 提供的功能，會協助您在 Office 方案中使用 Windows Form 控制項，但對 WPF 控制項則不提供類似的功能。 例如，您可以將 Windows Form 控制項加入文件和工作表在設計階段拖曳控制項從**工具箱**，或在執行階段使用 helper 方法。 不過，WPF 控制項無法使用這些工具。  
  
 WPF 控制項將 <xref:System.Windows.Forms.Integration.ElementHost> 類別用做 Windows Form 控制項或表單和 WPF 控制項之間的整合層。 當您在設計階段將 WPF 控制項加入解決方案時，Visual Studio 會為您自動產生 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
## <a name="wpf-resources"></a>WPF 資源  
 如需在 Windows Form 控制項和表單上裝載 WPF 控制項的架構和設計問題的詳細資訊，請參閱下列主題：  
  
-   [Windows Forms 和 WPF 互通性輸入架構](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Windows Forms 和 WPF 屬性對應](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [WPF 和 Windows Forms 互通](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Windows Form 控制項和對等 WPF 控制項](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 如需在設計階段於 Visual Studio 的 Windows Form 控制項和表單中加入 WPF 控制項的詳細資訊，請參閱下列主題：  
  
-   [逐步解說：在設計階段建立 Windows Forms 的新 WPF 內容](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [逐步解說：在設計階段排列 Windows Forms 的 WPF 內容](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [逐步解說：設定 WPF 內容的樣式](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>請參閱  
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [Windows Form 控制項，在 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [自訂工作窗格](../vsto/custom-task-panes.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何： 應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [如何：在 Outlook 增益集專案中新增表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  