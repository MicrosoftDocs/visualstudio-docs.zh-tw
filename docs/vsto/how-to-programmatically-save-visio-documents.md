---
title: 如何：以程式設計方式儲存 Visio 檔
description: 瞭解如何使用 Visual Studio 以程式設計方式儲存尚未儲存的 Microsoft Visio 現有檔和新檔。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 340d813a19c0c0dc5c347d3cfe4c7b29ff1bd049
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828991"
---
# <a name="how-to-programmatically-save-visio-documents"></a>如何：以程式設計方式儲存 Visio 檔
  儲存 Microsoft Office Visio 文件的方式有很多種：

- 在現有的文件中儲存變更。

- 儲存新的文件，或以新名稱儲存文件。

- 以指定的引數儲存文件。

  如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) 方法、 [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) 方法和 [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) 方法的 VBA 參考文件。

## <a name="save-an-existing-document"></a>儲存現有檔

### <a name="to-save-a-document"></a>儲存文件

- 呼叫已儲存過文件之 `Microsoft.Office.Tools.Visio.Document` 類別的 `Microsoft.Office.Interop.Visio.Document.Save` 方法。

     若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

    > [!NOTE]
    > 如果尚未儲存新的 Visio 文件，`Microsoft.Office.Interop.Visio.Document.Save` 方法會擲回例外狀況。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet11":::

## <a name="save-a-document-with-a-new-name"></a>使用新名稱儲存檔
 使用 `Microsoft.Office.Interop.Visio.Document.SaveAs` 方法儲存新的文件或有新名稱的文件。 這個方法需要指定新的檔案名稱。

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>以新名稱儲存使用中的 Visio 文件

- 使用包括檔案名稱的完整路徑呼叫您要儲存之 `Microsoft.Office.Tools.Visio.Document` 的 `Microsoft.Office.Interop.Visio.Document.SaveAs` 方法。 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。

     若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet10":::

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>使用新名稱和指定的引數儲存檔
 使用 `Microsoft.Office.Interop.Visio.Document.SaveAsEx` 方法儲存具有新名稱的文件，並指定所有適用的引數套用至文件。

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>以新名稱和指定的引數儲存文件

- 使用包括檔案名稱的完整路徑呼叫您要儲存之 `Microsoft.Office.Tools.Visio.Document` 的 `Microsoft.Office.Interop.Visio.Document.SaveAsEx` 方法。 如果該資料夾中已有同名的檔案，即擲回例外狀況。

     下列程式碼範例會以新名稱儲存使用中的文件、將文件標示為唯讀，以及在 [最近使用的清單] 中顯示文件。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="compile-the-code"></a>編譯程式碼
 這段程式碼範例需要下列項目：

- 若要儲存具有新名稱的檔，名為的目錄 `Test` 必須位於 WINDOWS XP 和舊版) 的 *我的檔* 資料夾 (，或適用于 windows Vista) 的 [ *檔* ] 資料夾 (。

## <a name="see-also"></a>另請參閱
- [Visio 方案](../vsto/visio-solutions.md)
- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)
- [如何：以程式設計方式建立新的 Visio 檔](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [如何：以程式設計方式開啟 Visio 檔](../vsto/how-to-programmatically-open-visio-documents.md)
- [如何：以程式設計方式關閉 Visio 檔](../vsto/how-to-programmatically-close-visio-documents.md)
- [如何：以程式設計方式列印 Visio 檔](../vsto/how-to-programmatically-print-visio-documents.md)
