---
title: 逐步解說：使用選項按鈕更新檔中的圖表
description: 瞭解如何在 Microsoft Word 的檔層級自訂中使用選項按鈕，讓使用者可以選擇在檔上選取圖表樣式。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4d6689d82051ef5f8c887c19ec91cbb6d513b8b8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828198"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>逐步解說：使用選項按鈕更新檔中的圖表
  本逐步解說示範如何在 Microsoft Office Word 的文件層級自訂中使用選項按鈕，讓使用者可以在文件上選取圖表樣式。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 本逐步解說將說明下列工作：

- 在設計階段，將圖表加入至文件層級專案中的文件。

- 透過將選項按鈕加入至使用者控制項來分組選項按鈕。

- 當選取選項時變更圖表樣式。

  若要以完整範例的形式查看結果，請參閱 [Office 開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中的 Word 控制項範例。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 第一個步驟是建立 Windows 文件專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立具有 **My Chart 選項** 名稱的 Word 檔專案。 在嚮導中，選取 [ **建立新檔**]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Word 檔，並將 [ **我的圖表選項** ] 專案加入 **方案總管**。

## <a name="add-a-chart-to-the-document"></a>將圖表加入至檔

### <a name="to-add-a-chart"></a>加入圖表

1. 在 Visual Studio 設計工具所裝載的 Word 檔中，按一下功能區上的 [ **插入** ] 索引標籤。

2. 在 [ **文字** ] 群組中，按一下 [ **插入物件** ] 下拉式按鈕，然後按一下 [ **物件**]。

     [ **物件** ] 對話方塊隨即開啟。

3. 在 [**建立新** 索引標籤] 的 [**物件類型**] 清單中，選取 [ **Microsoft Graph 圖表**]，然後按一下 **[確定]**。

     在插入點將圖表加入至檔，[資料工作 **表** ] 視窗隨即出現，其中包含一些預設資料。

4. 關閉 [資料工作 **表** ] 視窗以接受圖表中的預設值，然後按一下檔內部，將焦點移離圖表。

5. 以滑鼠右鍵按一下圖表，然後按一下 [ **格式化物件**]。

6. 在 [**格式物件**]**對話方塊的 [配置] 索引** 標籤上，選取 [**正方形**]，然後按一下 **[確定]**。

## <a name="add-a-user-control-to-the-project"></a>將使用者控制項新增至專案
 文件上的選項按鈕預設並不會互斥。 若要讓選項按鈕正常運作，您可以將選項按鈕加入至使用者控制項，再撰寫程式碼以控制選取範圖。

### <a name="to-add-a-user-control"></a>若要加入使用者控制項

1. 在 **方案總管** 中選取 [**我的圖表選項**] 專案。

2. 在 [專案] 功能表上，按一下 [加入新項目]。

3. 在 [ **加入新專案** ] 對話方塊中，按一下 [ **使用者控制項**]，將控制項命名為 **ChartOptions，** 然後按一下 [ **加入**]。

### <a name="to-add-windows-form-controls-to-the-user-control"></a>將 Windows Form 控制項加入至使用者控制項

1. 如果在設計工具中看不到使用者控制項，請按兩下 **方案總管** 中的 [ **ChartOptions** ]。

2. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將第一個 **選項按鈕** 控制項拖曳至使用者控制項，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**columnChart**|
    |**Text**|**直條圖**|

3. 將第二個 **選項按鈕** 加入至使用者控制項，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**barChart**|
    |**Text**|**長條圖**|

4. 將第三個 **選項按鈕** 加入至使用者控制項，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**lineChart**|
    |**Text**|**折線圖**|

5. 將第四個 **選項按鈕** 加入至使用者控制項，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**areaBlockChart**|
    |**Text**|**區塊圖**|

## <a name="add-references"></a>新增參考
 若要從檔的使用者控制項存取圖表，您必須 `Microsoft.Office.Interop.Graph` 在專案中有該元件的參考。

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>加入 Microsoft.Office.Interop.Graph 組件的參考

1. 在 [專案] 功能表上，按一下 [加入參考]。

     [新增參考] 對話方塊隨即出現。

2. 在 [ **.net** ] 索引標籤上，選取 [ **Microsoft** ]，然後按一下 **[確定]**。 選取版本為 14.0.0.0 的組件。

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>選取選項按鈕時變更圖表樣式
 若要讓按鈕正常運作，請在使用者控制項上建立公用事件，加入屬性以設定選取類型，並為各個選項按鈕建立 `CheckedChanged` 事件的程序。

### <a name="to-create-an-event-and-property-on-a-user-control"></a>在使用者控制項上建立事件和屬性

1. 在 **方案總管** 中，以滑鼠右鍵按一下使用者控制項，然後按一下 [ **視圖程式碼**]。

2. 將用於建立 `SelectionChanged` 事件和 `Selection` 屬性的程式碼加入至 `ChartOptions` 類別。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet9":::

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>處理選項按鈕的 CheckedChange 事件

1. 在 `CheckedChanged` 選項按鈕的 `areaBlockChart` 事件處理常式中設定圖表類型，然後再引發事件。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet10":::

2. 在 `CheckedChanged` 選項按鈕的 `barChart` 事件處理常式中設定圖表類型。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet11":::

3. 在 `CheckedChanged` 選項按鈕的 `columnChart` 事件處理常式中設定圖表類型。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet12":::

4. 在 `CheckedChanged` 選項按鈕的 `lineChart` 事件處理常式中設定圖表類型。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet13":::

5. 在 C# 中，您必須為選項按鈕加入事件處理常式。 您可以將程式碼加入至 `ChartOptions` 建構函式，放在 `InitializeComponent` 的呼叫下方。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet14":::

## <a name="add-the-user-control-to-the-document"></a>將使用者控制項新增至檔
 當您建立方案時，會自動將新的使用者控制項新增至 [ **工具箱**]。 然後，您可以將控制項從 [ **工具箱** ] 拖曳至檔。

### <a name="to-add-the-user-control-your-document"></a>將使用者控制項加入至您的文件

1. 在 [建置] 功能表上，按一下 [建置方案]。

     **ChartOptions** 使用者控制項就會加入至 [**工具箱**]。

2. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **ThisDocument** ] 或 [ **ThisDocument**]，然後按一下 [ **視圖設計** 工具]。

3. 將 `ChartOptions` 控制項從 [ **工具箱** ] 拖曳至檔。

     在 [ **屬性** ] 視窗中，將您剛剛新增的控制項命名為檔  `ChartOptions1` 。

## <a name="change-the-chart-type"></a>變更圖表類型
 建立事件處理常式，以根據在使用者控制項中選取的選項來變更圖表類型。

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>變更顯示在文件中的圖表類型

1. 將以下事件處理常式新增至 `ThisDocument` 類別。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet15":::

2. 在 C# 中，您必須將使用者控制項的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet16":::

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試文件，確定是否在選取選項按鈕時正確更新圖表樣式。

### <a name="to-test-your-document"></a>測試文件

1. 按 **F5** 執行您的專案。

2. 選取不同的選項按鈕。

3. 確認圖表樣式的變更與所選的項目相符。

## <a name="next-steps"></a>下一步
 接著可以執行下列一些工作：

- 使用按鈕填入文字方塊。 如需詳細資訊，請參閱 [逐步解說：使用按鈕在檔的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。

- 從下拉式方塊選取樣式，以變更格式。 如需詳細資訊，請參閱 [逐步解說：使用 CheckBox 控制項變更檔案格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。

## <a name="see-also"></a>另請參閱
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [Office 檔上 Windows Forms 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
