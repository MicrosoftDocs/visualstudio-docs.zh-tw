---
title: 使用 VSTO 增益集將自訂 XML 元件新增至檔
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92c00ea69069b7374f5f595cc6f198aac23d1f91
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538290"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>如何：使用 VSTO 增益集將自訂 XML 元件新增至檔
  您可以將 XML 資料儲存在下列類型的文件中，方法是在 VSTO 增益集中建立自訂 XML 組件：

- Microsoft Office Excel 活頁簿。

- Microsoft Office Word 文件。

- Microsoft Office PowerPoint 簡報。

  如需詳細資訊，請參閱[自訂 XML 元件總覽](../vsto/custom-xml-parts-overview.md)。

  **適用對象：** 本主題資訊適用於 Excel、PowerPoint 和 Word 應用程式層級專案。 如需詳細資訊，請參閱[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>將自訂 XML 組件加入至 Excel 活頁簿

1. 將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至活頁簿中的 <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在活頁簿中的 XML 字串。

     下列程式碼範例會將自訂 XML 組件加入至指定的活頁簿。

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2. 將 `AddCustomXmlPartToWorkbook` 方法新增至 `ThisAddIn` Excel VSTO 增益集專案中的類別。

3. 從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟活頁簿時建立自訂 XML 組件，請從 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 事件的事件處理常式呼叫方法。

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>將自訂 XML 組件加入至 Word 文件

1. 將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至文件中的 <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在文件中的 XML 字串。

     下列程式碼範例會將自訂 XML 組件加入至指定的文件。

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2. 將 `AddCustomXmlPartToDocument` 方法新增至 `ThisAddIn` Word VSTO 增益集專案中的類別。

3. 從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟文件時建立自訂 XML 組件，請從 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件的事件處理常式呼叫方法。

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>將自訂 XML 組件加入至 PowerPoint 簡報

1. 在簡報中，將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入[_Presentation 至 CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29)集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在簡報中的 XML 字串。

     下列程式碼範例會將自訂 XML 組件加入至指定的簡報。

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2. `AddCustomXmlPartToPresentation` `ThisAddIn` 在 POWERPOINT 的 VSTO 增益集專案中，將方法新增至類別。

3. 從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟簡報時建立自訂 XML 元件，請從 AfterPresentationOpen 事件的事件處理[EApplication_Event](/previous-versions/office/developer/office-2010/ff762843(v=office.14))程式呼叫方法。

## <a name="robust-programming"></a>穩固程式設計
 為了簡單起見，這個範例使用定義為方法中區域變數的 XML 字串。 通常，您應從外部來源取得 XML，例如檔案或資料庫。

## <a name="see-also"></a>另請參閱
- [自訂 XML 元件總覽](../vsto/custom-xml-parts-overview.md)
- [如何：將自訂 XML 元件加入至檔層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
