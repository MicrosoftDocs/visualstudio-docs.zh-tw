---
title: 如何：快取受密碼保護檔中的資料
description: 瞭解如果您將資料加入至以密碼保護的檔或活頁簿中的資料快取，您可以藉由覆寫專案中的兩個方法來儲存快取資料的變更。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ccdb906022d4dcfc321af294eec59afa36832773
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824181"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>如何：快取受密碼保護檔中的資料
  如果您將資料加入至以密碼保護的檔或活頁簿中的資料快取，系統不會自動儲存對快取資料的變更。 您可以藉由覆寫專案中的兩個方法，來儲存快取資料的變更。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Word 檔中的快取

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>若要在以密碼保護的 Word 檔中快取資料

1. 在 `ThisDocument` 類別中，將公用欄位或屬性標示為快取。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。

2. 覆寫 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 類別中的方法 `ThisDocument` ，並從檔中移除保護。

     儲存檔時，會 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 呼叫這個方法，讓您有機會取消保護檔。 這可讓您儲存快取資料的變更。

3. 覆寫 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 類別中的方法 `ThisDocument` ，並將保護重新套用至檔。

     檔儲存之後，會 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 呼叫這個方法，讓您有機會將保護重新套用至檔。

### <a name="example"></a>範例
 下列程式碼範例示範如何在以密碼保護的 Word 檔中快取資料。 在程式碼移除方法中的保護之前，會儲存 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 目前的 <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> 值，以便在方法中重新套用相同類型的保護 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 。

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb" id="Snippet1":::

### <a name="compile-the-code"></a>編譯程式碼
 將此程式碼新增至 `ThisDocument` 專案中的類別。 這段程式碼假設密碼是儲存在名為的欄位中 `securelyStoredPassword` 。

## <a name="cache-in-excel-workbooks"></a>Excel 活頁簿中的快取
 在 Excel 專案中，只有當您使用方法以密碼保護整個活頁簿時，才需要此程式 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 。 如果您使用方法只以密碼保護特定工作表，就不需要執行此程式 <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> 。

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>若要在使用密碼保護的 Excel 活頁簿中快取資料

1. 在 `ThisWorkbook` 類別或其中一個 `Sheet` *n* 類別中，將公用欄位或屬性標示為快取。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。

2. 覆寫 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 類別中的方法 `ThisWorkbook` ，並從活頁簿移除保護。

     儲存活頁簿時，會 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 呼叫這個方法，讓您有機會取消保護活頁簿。 這可讓您儲存快取資料的變更。

3. 覆寫 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 類別中的方法 `ThisWorkbook` ，並將保護重新套用至檔。

     儲存活頁簿之後，會 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 呼叫這個方法，讓您有機會將保護重新套用至活頁簿。

### <a name="example"></a>範例
 下列程式碼範例示範如何在以密碼保護的 Excel 活頁簿中快取資料。 在程式碼移除方法中的保護之前，會儲存 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 目前的 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> 和 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> 值，以便在方法中重新套用相同類型的保護 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 。

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs" id="Snippet1":::

### <a name="compile-the-code"></a>編譯程式碼
 將此程式碼新增至 `ThisWorkbook` 專案中的類別。 這段程式碼假設密碼是儲存在名為的欄位中 `securelyStoredPassword` 。

## <a name="see-also"></a>另請參閱
- [快取資料](../vsto/caching-data.md)
- [如何：快取資料供離線使用或在伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [如何：以程式設計方式快取 Office 檔中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
