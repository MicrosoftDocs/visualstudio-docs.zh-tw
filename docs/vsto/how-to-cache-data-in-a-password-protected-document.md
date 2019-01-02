---
title: HOW TO：在受密碼保護的文件中的快取資料
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 21e2b0501b96a1c04cee72487678b3e909440fb4
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647287"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>HOW TO：在受密碼保護的文件中的快取資料
  如果您將資料加入文件或密碼保護的活頁簿中的資料快取時，會不會自動儲存變更快取的資料。 您可以藉由覆寫專案中的兩個方法，來快取的資料儲存變更。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Word 文件中的快取  
  
### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>以密碼保護的 Word 文件中的快取資料  
  
1.  在 `ThisDocument`類別，並將標示將公用欄位或快取的屬性。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。  
  
2.  覆寫<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>方法中的`ThisDocument`類別，並從文件移除保護。  
  
     儲存文件時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]呼叫這個方法，讓您有機會取消保護文件。 這可讓快取的資料儲存的變更。  
  
3.  覆寫<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>方法中的`ThisDocument`類別，並保護重新套用至文件。  
  
     在儲存文件之後，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]呼叫這個方法，讓您有機會保護重新套用至文件。  
  
### <a name="example"></a>範例  
 下列程式碼範例示範如何快取受密碼保護的 Word 文件中的資料。 程式碼會移除的保護之前<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>方法，它會儲存目前<xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A>值，以便可以重新套用相同的保護類型，在<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>方法。  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compile-the-code"></a>編譯程式碼  
 新增下列程式碼`ThisDocument`專案中的類別。 此程式碼會假設密碼會儲存在名為欄位`securelyStoredPassword`。  
  
## <a name="cache-in-excel-workbooks"></a>在 Excel 活頁簿中快取  
 在 Excel 專案中，此程序是必要的使用來保護整個活頁簿密碼時，才<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>方法。 此程序不需要使用保護特定工作表的密碼如果<xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>方法。  
  
### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>以密碼保護的 Excel 活頁簿中的快取資料  
  
1.  在 `ThisWorkbook`類別或其中一個`Sheet` *n*類別，將標記，將公用欄位或快取的屬性。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。  
  
2.  覆寫<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>方法中的`ThisWorkbook`類別，並移除活頁簿中的保護。  
  
     儲存活頁簿時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]呼叫這個方法，讓您有機會取消保護活頁簿。 這可讓快取的資料儲存的變更。  
  
3.  覆寫<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>方法中的`ThisWorkbook`類別，並保護重新套用至文件。  
  
     儲存活頁簿之後，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]呼叫這個方法，讓您有機會保護重新套用至活頁簿。  
  
### <a name="example"></a>範例  
 下列程式碼範例示範如何快取受密碼保護的 Excel 活頁簿中的資料。 程式碼會移除的保護之前<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>方法，它會儲存目前<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A>並<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A>值，以便可以重新套用相同的保護類型，在<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>方法。  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compile-the-code"></a>編譯程式碼  
 新增下列程式碼`ThisWorkbook`專案中的類別。 此程式碼會假設密碼會儲存在名為欄位`securelyStoredPassword`。  
  
## <a name="see-also"></a>另請參閱  
 [快取資料](../vsto/caching-data.md)   
 [如何：離線或在伺服器上快取資料以供使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：以程式設計方式快取 Office 文件中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  