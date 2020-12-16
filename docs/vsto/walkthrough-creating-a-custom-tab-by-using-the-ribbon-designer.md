---
title: 逐步解說：使用功能區設計工具建立自訂索引標籤
description: 瞭解如何使用功能區設計工具建立自訂索引標籤，然後在其上新增控制項並放置控制項。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 539f75b7770abab75e912a28bc62ed51b7fb61d8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524829"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>逐步解說：使用功能區設計工具建立自訂索引標籤
  您可以使用功能區設計工具，建立自訂索引標籤，然後在其上加入和放置控制項。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 本逐步解說將說明下列工作：

- [建立執行窗格](#BKMK_CreateActionsPanes)。

- [建立自訂](#BKMK_CreateCustomTab)索引標籤。

- [使用 [自訂] 索引標籤上的按鈕，隱藏和顯示執行窗格](#BKMK_HideShowActionsPane)。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>建立 Excel 活頁簿專案
 所有 Office 應用程式使用功能區設計工具的步驟大部分相同。 這個範例會使用 Excel 活頁簿。

### <a name="to-create-an-excel-workbook-project"></a>建立 Excel 活頁簿專案

- 使用名稱 **MyExcelRibbon** 建立 Excel 活頁簿專案。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的活頁簿，並將 **MyExcelRibbon** 專案加入 **方案總管**。

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> 建立動作窗格
 將兩個自訂的執行窗格加入至專案。 您稍後會將兩個用來顯示和隱藏這些執行窗格的按鈕加入至自訂索引標籤。

### <a name="to-create-actions-panes"></a>建立執行窗格

1. 在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。

2. 在 [ **加入新專案** ] 對話方塊中，選取 [ **ActionsPaneControl**]，然後選擇 [ **加入**]。

     **ActionsPaneControl1.cs** 或 **ActionsPaneControl1 .vb** 檔案會在設計工具中開啟。

3. 從 [工具箱] 的 [ **通用控制項** ] 索引標籤中，將標籤加入至設計 **工具** 介面。

4. 在 [ **屬性** ] 視窗中，將 [label1] 的 [ **Text** ] 屬性設定為 [ **動作窗格 1**]。

5. 重複步驟 1 到 5，建立第二個執行窗格和標籤。 將第二個標籤的 [ **Text** ] 屬性設定為 [ **動作] 窗格 2**。

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> 建立自訂索引標籤
 其中一個 Office 應用程式設計方針是使用者應一律具有 Office 應用程式 UI 的控制項。 若要為執行窗格加入這個功能，您可以加入顯示和隱藏功能區上自訂索引標籤的每個執行窗格的按鈕。 若要建立自訂索引標籤，請將 **功能區 (視覺化設計工具)** 專案加入至專案。 設計工具可協助您加入及定位控制項、設定控制項屬性及處理控制項事件。

### <a name="to-create-a-custom-tab"></a>建立自訂索引標籤

1. 在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。

2. 選取 [ **加入新項目** ] 對話方塊中的 [ **功能區 (視覺化設計工具)**]。

3. 將新功能區的名稱變更為 **myribbon.vb**，然後選擇 [ **加入**]。

     **MyRibbon.cs** 或 **MyRibbon.vb** 檔案會在功能區設計工具中開啟，並顯示預設索引標籤和群組。

4. 在 [功能區設計工具] 中，選擇預設索引標籤。

5. 在 [ **屬性** ] 視窗中，展開 [ **ControlId** ] 屬性，然後將 [ **ControlIdType** ] 屬性設定為 [ **自訂**]。

6. 將 [ **標籤** ] 屬性設定為 [ **自訂]** 索引標籤。

7. 在功能區設計工具中，選擇 [ **group1**]。

8. 在 [ **屬性** ] 視窗中，將 [ **標籤** ] 設定為 [ **動作] 窗格管理員**。

9. 從 [**工具箱**] 的 [ **Office 功能區控制項**] 索引標籤中，將按鈕拖曳至 [ **group1**]。

10. 選取 [ **button1**]。

11. 在 [ **屬性** ] 視窗中，設定 **標籤** 以 **顯示動作窗格 1**。

12. 將第二個按鈕加入 [ **Group1**]，並將 [ **標籤** ] 屬性設定為 **顯示動作窗格 2**。

13. 從 [**工具箱**] 的 [ **Office 功能區控制項**] 索引標籤，將 **切換按鈕** 控制項拖曳至 [ **group1**]。

14. 將 [ **標籤** ] 屬性設定為 **隱藏 [動作] 窗格**。

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> 使用 [自訂] 索引標籤上的按鈕隱藏和顯示動作窗格
 最後一個步驟是加入回應使用者的程式碼。 針對兩個按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 事件和切換按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件加入事件處理常式。 將程式碼加入至這些事件處理常式以啟用隱藏和顯示執行窗格。

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>使用自訂索引標籤中的按鈕隱藏和顯示執行窗格

1. 在 **方案總管** 中，開啟 [ *MyRibbon.cs* ] 或 [ *myribbon.vb*] 的快捷方式功能表，然後選擇 [ **視圖程式碼**]。

2. 將下列程式碼加入至 `MyRibbon` 類別的頂端。 這個程式碼會建立兩個執行窗格物件。

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. 以下列程式碼取代 `MyRibbon_Load` 方法。 這個程式碼會將執行窗格物件加入至 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 集合，並且隱藏物件不提供檢視。 Visual C# 程式碼也會將委派附加至數個功能區控制項事件。

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. 將下列三個事件處理常式方法加入至 `MyRibbon` 類別。 這些方法會處理兩個按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 事件及切換按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件。 button1 和 button2 的事件處理常式會顯示交替的執行窗格。 toggleButton1 的事件處理常式則會顯示和隱藏作用中的執行窗格。

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>測試自訂索引標籤
 當您執行專案時，Excel 會啟動，而 [ **我的自訂** 索引標籤] 索引標籤會出現在功能區。 選擇 [我的 **自訂]** 索引標籤上的按鈕，以顯示和隱藏 [動作] 窗格。

### <a name="to-test-the-custom-tab"></a>測試自訂索引標籤

1. 按 **F5** 執行您的專案。

2. 選擇 [ **我的自訂** 索引標籤] 索引標籤。

3. 在 [ **自訂動作窗格管理員]** 群組中，選擇 [ **顯示動作窗格 1]**。

     [動作] 窗格隨即出現，並顯示標籤 **動作窗格 1**。

4. 選擇 [ **顯示動作窗格 2]**。

     [動作] 窗格隨即出現，並顯示標籤 **動作窗格 2**。

5. 選擇 [ **隱藏動作] 窗格**。

     執行窗格將不再顯示。

## <a name="next-steps"></a>後續步驟
 您可以透過下列主題，進一步了解自訂 Office UI 的方式：

- 將內容為主的 UI 加入至任何文件層級的自訂。 如需詳細資訊，請參閱執行 [窗格總覽](../vsto/actions-pane-overview.md)。

- 展開標準或自訂的 Microsoft Office Outlook 表單。 如需詳細資訊，請參閱 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。

## <a name="see-also"></a>另請參閱
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
- [功能區總覽](../vsto/ribbon-overview.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [如何：變更功能區上的索引標籤位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)
- [如何：將控制項加入至 backstage 視圖](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)
