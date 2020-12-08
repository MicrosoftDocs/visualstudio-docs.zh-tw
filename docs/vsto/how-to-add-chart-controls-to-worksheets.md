---
title: 如何：將圖表控制項加入至工作表
description: 瞭解如何在設計階段和執行時間于檔層級自訂中，將圖表控制項加入 Microsoft Office Excel 工作表。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7e48b8cfbcf4ee1c7340aef4cd59e09698f89412
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845462"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>如何：將圖表控制項加入至工作表
  您可以在 <xref:Microsoft.Office.Tools.Excel.Chart> 設計階段和執行時間的檔層級自訂中，將控制項加入 Microsoft Office Excel 工作表。 您也可以在 <xref:Microsoft.Office.Tools.Excel.Chart> VSTO 增益集的執行時間加入控制項。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 本主題說明下列工作：

- [在設計階段加入圖表控制項](#designtime)

- [在檔層級專案中，于執行時間加入圖表控制項](#runtimedoclevel)

- [在執行時間于 VSTO 增益集專案中加入圖表控制項](#runtimeaddin)

  如需控制項的詳細資訊 <xref:Microsoft.Office.Tools.Excel.Chart> ，請參閱 [Chart 控制項](../vsto/chart-control.md)。

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> 在設計階段加入圖表控制項
 您可以採用您從應用程式中加入圖表的方式，將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入工作表。

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.Chart>控制項無法在 [**工具箱**] 或 [**資料來源**] 視窗中使用。

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>將圖表主控制項加入 Excel 工作表

1. 在 [ **插入** ] 索引標籤的 [ **圖表** ] 群組中，按一下 [資料 **行**]，按一下圖表的類別，然後按一下您想要的圖表類型。

2. 在 [ **插入圖表** ] 對話方塊中，按一下 **[確定]**。

3. 在 [ **設計** ] 索引標籤的 [ **資料** ] 群組中，按一下 [ **選取資料**]。

4. 在 [**選取資料來源**] 對話方塊中，按一下 [**圖表****資料範圍**] 方塊，並清除任何預設選項。

5. 在 [ **圖表的資料** ] 工作表中，選取包含圖表之資料的資料格範圍 (資料格 **A5** 到 **D8**) 。

6. 在 [ **選取資料來源** ] 對話方塊中，按一下 **[確定]**。

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> 在檔層級專案中，于執行時間加入圖表控制項
 您可以在執行階段，以動態方式加入 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。 當文件關閉時，動態建立的圖表便不再是文件中的主控制項。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>以程式設計方式將圖表控制項加入工作表

1. 在 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件處理常式中插入下列程式碼，以加入 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> 在執行時間于 VSTO 增益集專案中加入圖表控制項
 您可以利用程式設計方式，在 VSTO 增益集專案中，將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入任何開啟中的工作表。 如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

 當工作表關閉時，動態建立的圖表控制項便不再是工作表中的主控制項。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>以程式設計方式將圖表控制項加入工作表

1. 下列程式碼會產生開啟中之工作表的主項目，然後新增 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要：

- 要繪製成圖表的資料，即工作表中 A5 到 D8 之間的範圍。

## <a name="see-also"></a>另請參閱
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [Chart 控制項](../vsto/chart-control.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
