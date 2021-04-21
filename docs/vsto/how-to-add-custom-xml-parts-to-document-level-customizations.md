---
title: 如何：將自訂 XML 元件加入至檔層級自訂
description: 瞭解如何在檔層級自訂中建立自訂 XML 元件，以便將 XML 資料儲存在 Microsoft Office Excel 活頁簿或 Microsoft Office Word 檔中。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99374a2daded3c4b49b60053a69cd1ff7c4dffe8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827679"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>如何：將自訂 XML 元件加入至檔層級自訂
  您可以在文件層級自訂中建立自訂 XML 組件，將 XML 資料儲存在 Microsoft Office Excel 活頁簿或 Microsoft Office Word 文件中。 如需詳細資訊，請參閱 [自訂 XML 元件總覽](../vsto/custom-xml-parts-overview.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio 不提供 Microsoft Office PowerPoint 的文件層級專案。 如需使用 VSTO 增益集將自訂 XML 元件加入至 PowerPoint 簡報的詳細資訊，請參閱 [如何：使用 Vsto 增益集將自訂 xml 元件加入至檔](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)。

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>將自訂 XML 組件加入至 Excel 活頁簿

1. 將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至活頁簿中的 <xref:Microsoft.Office.Core.CustomXMLParts> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在活頁簿中的 XML 字串。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. 將 `AddCustomXmlPartToWorkbook` 方法加入 Excel 文件層級專案中的 `ThisWorkbook` 類別。

3. 從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟活頁簿時建立自訂 XML 組件，請從 `ThisWorkbook_Startup` 事件處理常式呼叫方法。

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>將自訂 XML 組件加入至 Word 文件

1. 將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 物件加入至文件中的 <xref:Microsoft.Office.Core.CustomXMLParts> 集合。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含您要儲存在文件中的 XML 字串。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. 將 `AddCustomXmlPartToDocument` 方法加入 Word 文件層級專案中的 `ThisDocument` 類別。

3. 從專案中的其他程式碼呼叫方法。 例如，若要在使用者開啟文件時建立自訂 XML 組件，請從 `ThisDocument_Startup` 事件處理常式呼叫方法。

## <a name="robust-programming"></a>穩固程式設計
 為了簡單起見，這個範例使用定義為方法中區域變數的 XML 字串。 通常，您應從外部來源取得 XML，例如檔案或資料庫。

## <a name="see-also"></a>另請參閱
- [自訂 XML 元件總覽](../vsto/custom-xml-parts-overview.md)
- [如何：使用 VSTO 增益集將自訂 XML 元件新增至檔](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
