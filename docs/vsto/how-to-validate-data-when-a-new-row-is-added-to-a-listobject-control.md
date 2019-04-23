---
title: HOW TO：新的資料列加入 ListObject 控制項時驗證資料
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8aefab319b9b197b9b7df0e23fec71aa3cb64d1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039307"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>HOW TO：新的資料列加入 ListObject 控制項時驗證資料
  使用者可以將新的資料列加入繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。 您可以先驗證使用者的資料，再認可資料來源的變更。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>資料驗證
 每次將資料列加入繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject> ，就會引發 <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> 事件。 您可以處理這個事件以執行資料驗證。 例如，如果您的應用程式需要只有 65 年滿 18 歲之間的員工，可以加入資料來源，請確認輸入的年齡落在該範圍內加入資料列之前。

> [!NOTE]
>  除用戶端之外，亦請一律檢查伺服器上的使用者輸入。 如需詳細資訊，請參閱 <<c0> [ 安全的用戶端應用程式](/dotnet/framework/data/adonet/secure-client-applications)。

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>在新資料列加入資料繫結的 ListObject 時驗證資料

1. 在類別層級建立識別碼和 <xref:System.Data.DataTable> 的變數。

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. 建立新<xref:System.Data.DataTable>並新增範例資料行和資料`Startup`事件處理常式`Sheet1`類別 （在文件層級專案中） 或`ThisAddIn`類別 （在 VSTO 增益集專案中）。

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. 在 `list1_BeforeAddDataBoundRow` 事件處理常式中加入程式碼，以檢查輸入的年齡是否落在可接受的範圍內。

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>編譯程式碼
 這個程式碼範例假設在這個程式碼出現的工作表中已有名為 <xref:Microsoft.Office.Tools.Excel.ListObject> 的 `list1` 。

## <a name="see-also"></a>另請參閱
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject 控制項](../vsto/listobject-control.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [如何：將 ListObject 欄對應到資料](../vsto/how-to-map-listobject-columns-to-data.md)
