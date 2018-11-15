---
title: 如何： 使用 VSTO 增益集將自訂 XML 組件新增至文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a559f8c074a7e80ea898f86dc205dec6ad2bb064
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826892"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>如何： 使用 VSTO 增益集將自訂 XML 組件新增至文件
  您可以將 XML 資料儲存在下列類型的文件中，方法是在 VSTO 增益集中建立自訂 XML 組件：  
  
- Microsoft Office Excel 活頁簿。  
  
- Microsoft Office Word 文件。  
  
- Microsoft Office PowerPoint 簡報。  
  
  如需詳細資訊，請參閱 <<c0> [ 自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)。  
  
  **適用對象：** 本主題資訊適用於 Excel、PowerPoint 和 Word 應用程式層級專案。 如需詳細資訊，請參閱 <<c0> [ 依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。  
  
## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>將自訂 XML 組件加入至 Excel 活頁簿  
  
1.  將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至活頁簿中的 <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在活頁簿中的 XML 字串。  
  
     下列程式碼範例會將自訂 XML 組件加入至指定的活頁簿。  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  新增`AddCustomXmlPartToWorkbook`方法，以`ThisAddIn`Excel 的 VSTO 增益集專案中的類別。  
  
3.  從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟活頁簿時建立自訂 XML 組件，請從 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 事件的事件處理常式呼叫方法。  
  
## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>將自訂 XML 組件加入至 Word 文件  
  
1.  將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至文件中的 <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在文件中的 XML 字串。  
  
     下列程式碼範例會將自訂 XML 組件加入至指定的文件。  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  新增`AddCustomXmlPartToDocument`方法，以`ThisAddIn`Word VSTO 增益集專案中的類別。  
  
3.  從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟文件時建立自訂 XML 組件，請從 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件的事件處理常式呼叫方法。  
  
## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>將自訂 XML 組件加入至 PowerPoint 簡報  
  
1.  加入新<xref:Microsoft.Office.Core.CustomXMLPart>物件至[Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29)展示檔中的集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在簡報中的 XML 字串。  
  
     下列程式碼範例會將自訂 XML 組件加入至指定的簡報。  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  新增`AddCustomXmlPartToPresentation`方法，以`ThisAddIn`PowerPoint VSTO 增益集專案中的類別。  
  
3.  從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟簡報時，請建立自訂 XML 組件，從事件處理常式中呼叫方法[Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14))事件。  
  
## <a name="robust-programming"></a>穩固程式設計  
 為了簡單起見，這個範例使用定義為方法中區域變數的 XML 字串。 通常，您應從外部來源取得 XML，例如檔案或資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)   
 [如何： 將自訂 XML 組件新增至文件層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  