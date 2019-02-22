---
title: HOW TO：以程式設計方式列印 Visio 文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9a949ee781652c3e19b3ebc3476e736374fe4f21
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634314"
---
# <a name="how-to-programmatically-print-visio-documents"></a>HOW TO：以程式設計方式列印 Visio 文件
  您可以列印整份 Microsoft Office Visio 文件，或僅列印特定頁面。

 如需此列印方法的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) 方法和 [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) 方法的 VBA 參考文件。

## <a name="print-a-visio-document"></a>列印 Visio 文件

### <a name="to-print-a-complete-document"></a>列印整份文件

-   呼叫您要列印之 `Microsoft.Office.Interop.Visio.Document.Print` 物件的 `Microsoft.Office.Interop.Visio.Document` 方法。

     下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>列印 Visio 文件頁面

### <a name="to-print-a-page-of-a-document"></a>列印文件頁面

-   呼叫您要列印之 `Microsoft.Office.Interop.Visio.Pages.Print` 物件的 `Microsoft.Office.Interop.Visio.Pages` 方法。

     下列程式碼範例會列印使用中之文件的第一頁。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>另請參閱
- [Visio 方案](../vsto/visio-solutions.md)
- [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)
- [如何：以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [如何：以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)
- [如何：以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)
- [如何：以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)
