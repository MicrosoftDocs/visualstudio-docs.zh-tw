---
title: 如何：以程式設計方式建立新的 Visio 檔
description: 瞭解如何以程式設計方式建立新的 Microsoft Visio 繪圖檔案，並將它加入至 open Visio 檔的檔集合。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59c1fe0264a294692bea04b05e5e143fa28be801
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526848"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>如何：以程式設計方式建立新的 Visio 檔
  當您建立新的 Microsoft Office Visio 繪圖文件時，您會將它加入已開啟 Visio 文件的 `Microsoft.Office.Interop.Visio.Documents` 集合。 因此，`Microsoft.Office.Interop.Visio.Documents.Add` 方法會建立新的 Visio 繪圖文件。 如需詳細資訊，請參閱 Microsoft.Office.Interop.Visio.Documents.Add [myTemplate.vst](/office/vba/api/Visio.Documents.Add) 方法的 VBA 參考文件。

## <a name="create-new-blank-documents"></a>建立新的空白檔

### <a name="to-create-a-new-document"></a>建立新文件

- 使用 `Microsoft.Office.Interop.Visio.Documents.Add` 方法來建立不是以範本為基礎的空白新文件。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>建立從現有檔案複製的檔
 `Microsoft.Office.Interop.Visio.Documents.Add` 方法可建立現有 Visio 文件複本的新文件。 您必須提供圖表的檔案名稱和完整路徑。

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>建立從現有文件複製的新文件

- 呼叫 `Microsoft.Office.Interop.Visio.Documents.Add` 方法並指定 Visio 圖表的路徑。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>建立從現有的模版複製的樣板
 Microsoft.Office.Interop.Visio.Documents.Add [myTemplate.vst](/office/vba/api/Visio.Documents.Add) 方法可建立現有 Visio 樣板複本的新樣板。 您必須提供樣板的檔案名稱和完整路徑。

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>建立從現有樣板複製的新樣板

- 呼叫 `Microsoft.Office.Interop.Visio.Documents.Add` 方法並指定樣板的路徑。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>根據現有範本建立檔
 `Microsoft.Office.Interop.Visio.Documents.Add`方法可以建立新 *檔*， (以現有的 Visio (範本為基礎的 *.vsd* 檔案) ) 。 這個方法會複製屬於範本工作區一部分的樣板、樣式和設定。 您必須提供範本的檔案名稱和完整路徑。

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>建立以現有範本為基礎的新文件

- 呼叫 `Microsoft.Office.Interop.Visio.Documents.Add` 方法並指定範本的路徑。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

## <a name="compile-the-code"></a>編譯程式碼
 這段程式碼範例需要下列項目：

- 名為的 Visio 檔必須位在 `myDrawing.vsd` `Test` windows XP 和舊版) 的 *我的檔* 資料夾 (的目錄中，或是 windows Vista) 的 [ *檔* ] 資料夾 (。

- 名為的 Visio 檔必須位在 `myStencil.vss` `Test` windows XP 和舊版) 的 *我的檔* 資料夾 (的目錄中，或是 windows Vista) 的 [ *檔* ] 資料夾 (。

- 名為的 Visio 檔必須位在 `myTemplate.vst` `Test` windows XP 和舊版) 的 *我的檔* 資料夾 (的目錄中，或是 windows Vista) 的 [ *檔* ] 資料夾 (。

## <a name="see-also"></a>另請參閱
- [Visio 方案](../vsto/visio-solutions.md)
- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)
- [如何：以程式設計方式開啟 Visio 檔](../vsto/how-to-programmatically-open-visio-documents.md)
- [如何：以程式設計方式關閉 Visio 檔](../vsto/how-to-programmatically-close-visio-documents.md)
- [如何：以程式設計方式儲存 Visio 檔](../vsto/how-to-programmatically-save-visio-documents.md)
- [如何：以程式設計方式列印 Visio 檔](../vsto/how-to-programmatically-print-visio-documents.md)
