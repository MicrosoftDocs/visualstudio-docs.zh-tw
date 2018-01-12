---
title: "如何： 新的資料列加入 ListObject 控制項時驗證資料 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 509d298dc3ac10a91f2eb10aa8bcb26a9738f4d4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>如何：將新資料列加入 ListObject 控制項時驗證資料
  使用者可以將新的資料列加入繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。 您可以先驗證使用者的資料，再認可資料來源的變更。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>資料驗證  
 每次將資料列加入繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject> ，就會引發 <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> 事件。 您可以處理這個事件以執行資料驗證。 例如，如果應用程式要求加入資料來源的員工年紀必須介於 18 至 65 歲之間，您可以先確認輸入的年齡落在該範圍內，再加入資料列。  
  
> [!NOTE]  
>  除用戶端之外，亦請一律檢查伺服器上的使用者輸入。 如需詳細資訊，請參閱[安全用戶端應用程式](/dotnet/framework/data/adonet/secure-client-applications)。  
  
#### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>在新資料列加入資料繫結的 ListObject 時驗證資料  
  
1.  在類別層級建立識別碼和 <xref:System.Data.DataTable> 的變數。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  建立新的 <xref:System.Data.DataTable> ，並在 `Startup` 類別 (在文件層級專案中) 或 `Sheet1` 類別 (在 VSTO 增益集專案中) 的 `ThisAddIn` 事件處理常式中加入範例資料行和資料。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  在 `list1_BeforeAddDataBoundRow` 事件處理常式中加入程式碼，以檢查輸入的年齡是否落在可接受的範圍內。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例假設在這個程式碼出現的工作表中已有名為 <xref:Microsoft.Office.Tools.Excel.ListObject> 的 `list1` 。  
  
## <a name="see-also"></a>請參閱  
 [在執行階段擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在執行階段將控制項加入 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何：將 ListObject 欄對應到資料](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  