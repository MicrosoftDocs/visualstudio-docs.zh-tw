---
title: 如何：以程式設計方式儲存活頁簿
description: 以程式設計方式儲存 Microsoft Excel 活頁簿，而不變更路徑並儲存活頁簿的複本，而不需修改記憶體中開啟的活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4559d098a80a1dfd8f1d3f5c2c21cbebc992fcb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828978"
---
# <a name="how-to-programmatically-save-workbooks"></a>如何：以程式設計方式儲存活頁簿
  儲存活頁簿有好幾種方式。 您可以儲存活頁簿，而不變更路徑。 如果活頁簿先前沒有儲存過，則應該指定路徑來儲存活頁簿。 如果沒有明確指定路徑，Microsoft Office Excel 會將這個檔案以建立時指定的名稱儲存在目前的資料夾中。 您也可以儲存活頁簿的複本，而不修改記憶體中的已開啟活頁簿。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>儲存活頁簿而不變更路徑

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>儲存與文件層級自訂相關聯的活頁簿

1. 請呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> 類別的 `ThisWorkbook` 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>透過 VSTO 增益集儲存現用活頁簿

1. 請呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> 方法，即可儲存現用活頁簿。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>使用新路徑儲存活頁簿
 您可以將指定的活頁簿儲存至新位置或使用新名稱儲存，也可以選擇性地指定檔案格式、密碼、存取模式等項目。

> [!NOTE]
> 您可能會想要將此 <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> 屬性設定為 **False** ，然後再以新路徑儲存活頁簿，因為以某些格式儲存時需要互動。 將這個屬性設定為 **False** 會導致 Excel 使用所有預設值。

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>儲存與文件層級自訂相關聯的活頁簿

1. 請呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 類別的 `ThisWorkbook` 方法。 若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>透過 VSTO 增益集儲存現用活頁簿

1. 呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> 方法，即可將現用活頁簿儲存至新路徑。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>儲存活頁簿的複本
 您可以將活頁簿的複本儲存至檔案，而不修改記憶體中的已開啟活頁簿。 如果您要建立備份複本而不修改活頁簿的位置，這個方法就很有用。

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>儲存與文件層級自訂相關聯的活頁簿

1. 請呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> 類別的 `ThisWorkbook` 方法。 若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>透過 VSTO 增益集儲存現用活頁簿

1. 請呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> 方法，即可儲存現用活頁簿的複本。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>穩固程式設計
 以互動方式取消任何儲存或複製活頁簿的方法，都會在程式碼中引發執行階段錯誤。 例如，如果您的程式會呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 方法，但不會停用 Excel 的提示，而且您的使用者在出現提示時按一下 [ **取消** ]，則 Excel 會引發執行階段錯誤。

## <a name="see-also"></a>另請參閱
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [活頁簿主專案](../vsto/workbook-host-item.md)
- [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
