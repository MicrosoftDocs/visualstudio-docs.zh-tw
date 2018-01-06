---
title: "如何： 使用 VSTO 增益集將自訂 XML 組件加入文件 |Microsoft 文件"
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
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4f7c88ca0ef06ea74f6963166a2b6f421058c0da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>如何：使用 VSTO 增益集將自訂 XML 組件加入文件中
  您可以將 XML 資料儲存在下列類型的文件中，方法是在 VSTO 增益集中建立自訂 XML 組件：  
  
-   Microsoft Office Excel 活頁簿。  
  
-   Microsoft Office Word 文件。  
  
-   Microsoft Office PowerPoint 簡報。  
  
 如需詳細資訊，請參閱 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)。  
  
 **適用對象：** 本主題資訊適用於 Excel、PowerPoint 和 Word 應用程式層級專案。 如需詳細資訊，請參閱 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>將自訂 XML 組件加入至 Excel 活頁簿  
  
1.  將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至活頁簿中的 <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在活頁簿中的 XML 字串。  
  
     下列程式碼範例會將自訂 XML 組件加入至指定的活頁簿。  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  將 `AddCustomXmlPartToWorkbook` 方法加入 Excel VSTO 增益集專案中的 `ThisAddIn` 類別。  
  
3.  從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟活頁簿時建立自訂 XML 組件，請從 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 事件的事件處理常式呼叫方法。  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>將自訂 XML 組件加入至 Word 文件  
  
1.  將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至文件中的 <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在文件中的 XML 字串。  
  
     下列程式碼範例會將自訂 XML 組件加入至指定的文件。  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  將 `AddCustomXmlPartToDocument` 方法加入 Word VSTO 增益集專案中的 `ThisAddIn` 類別。  
  
3.  從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟文件時建立自訂 XML 組件，請從 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件的事件處理常式呼叫方法。  
  
### <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>將自訂 XML 組件加入至 PowerPoint 簡報  
  
1.  將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至簡報中的 <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在簡報中的 XML 字串。  
  
     下列程式碼範例會將自訂 XML 組件加入至指定的簡報。  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  將 `AddCustomXmlPartToPresentation` 方法加入 PowerPoint VSTO 增益集專案中的 `ThisAddIn` 類別。  
  
3.  從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟文件時建立自訂 XML 組件，請從 <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> 事件的事件處理常式呼叫方法。  
  
## <a name="robust-programming"></a>穩固程式設計  
 為了簡單起見，這個範例使用定義為方法中區域變數的 XML 字串。 通常，您應從外部來源取得 XML，例如檔案或資料庫。  
  
## <a name="see-also"></a>請參閱  
 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)   
 [如何：將自訂 XML 組件新增至文件層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  