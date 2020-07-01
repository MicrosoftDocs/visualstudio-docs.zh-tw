---
title: 如何：以程式設計方式開啟 Visio 檔
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb21d201c282461cbe82005f56bed023bb022209
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519986"
---
# <a name="how-to-programmatically-open-visio-documents"></a>如何：以程式設計方式開啟 Visio 檔
  有兩種方法可以開啟現有的 Microsoft Office Visio 檔：開啟和 Microsoft.office.interop.visio.documents.open。 Microsoft.office.interop.visio.documents.open 方法與 Open 方法完全相同，不同之處在于它會提供引數，供呼叫者指定檔開啟的方式。

 如需此物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) 方法和 [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) 方法的 VBA 參考文件。

## <a name="open-a-visio-document"></a>開啟 Visio 檔

### <a name="to-open-a-visio-document"></a>開啟 Visio 文件

- 呼叫 `Microsoft.Office.Interop.Visio.Documents.Open` 方法並提供 Visio 文件的完整路徑。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>使用指定的引數開啟 Visio 檔

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>開啟 Visio 文件為唯讀並停駐

- 呼叫 `Microsoft.Office.Interop.Visio.Documents.OpenEx` 方法，提供 Visio 文件的完整路徑，以及包含要使用的引數，在本例中為「停駐」和「唯讀」。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>編譯程式碼
 這段程式碼範例需要下列項目：

- 名為的 Visio 檔 `myDrawing.vsd` 必須位於 `Test` [*我的文件*] 資料夾（windows XP 及更早版本）或 [*檔*] 資料夾（windows Vista）中名為的目錄中。

## <a name="see-also"></a>另請參閱
- [Visio 解決方案](../vsto/visio-solutions.md)
- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)
- [如何：以程式設計方式建立新的 Visio 檔](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [如何：以程式設計方式關閉 Visio 檔](../vsto/how-to-programmatically-close-visio-documents.md)
- [如何：以程式設計方式儲存 Visio 檔](../vsto/how-to-programmatically-save-visio-documents.md)
- [如何：以程式設計方式列印 Visio 檔](../vsto/how-to-programmatically-print-visio-documents.md)
