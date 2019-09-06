---
title: HOW TO：以程式設計方式儲存檔
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4fbf8e4cb67d5216dc17c325911bb243fae6e1c
ms.sourcegitcommit: 5b34052a1c7d86179d7898ed532babb2d9dad4a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490614"
---
# <a name="how-to-programmatically-save-documents"></a>作法：以程式設計方式儲存檔

有數種方式可以儲存 Microsoft Office Word 檔。 您可以儲存檔, 而不需要變更檔的名稱, 也可以使用新名稱來儲存檔。

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>儲存檔, 而不變更名稱

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>儲存與檔層級自訂相關聯的檔

1. 請呼叫 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 類別的 <xref:Microsoft.Office.Tools.Word.Document> 方法。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>儲存使用中的檔

1. 呼叫現用<xref:Microsoft.Office.Interop.Word._Document.Save%2A>檔的方法。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   如果您不確定要儲存的檔是否為使用中的檔, 您可以使用其名稱來參考它。

### <a name="to-save-a-document-specified-by-name"></a>儲存依名稱指定的檔

1. 使用檔案名稱做為集合的<xref:Microsoft.Office.Interop.Word.Documents>引數。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>以新名稱儲存檔

`SaveAs`使用方法來儲存具有新名稱的檔。 您可以在檔層級 Word <xref:Microsoft.Office.Tools.Word.Document>專案中, 或在任何 Word 專案中使用原生<xref:Microsoft.Office.Interop.Word.Document>物件的這個主專案方法。 這個方法會要求您指定新的檔案名, 但其他引數則是選擇性的。

> [!NOTE]
> 如果您在的 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>事件處理常式`ThisDocument`中顯示 [SaveAs] 對話方塊, 並將 [*取消*] 參數設定為 [ **false**], 則應用程式可能會意外結束。 如果您將 [*取消*] 參數設定為 [ **true**], 則會出現錯誤訊息, 指出已停用自動儲存。

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>若要使用新名稱儲存與檔層級自訂相關聯的檔

1. 使用完整路徑和檔案名`ThisDocument` , 呼叫專案中類別的方法。`SaveAs` 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。 若要使用這個程式碼範例，請從 `ThisDocument` 類別執行程式碼。

    > [!NOTE]
    > 如果`SaveAs`目標目錄不存在, 或如果儲存檔案時發生其他問題, 方法就會擲回例外狀況。 最好的作法是在`try...catch` `SaveAs`方法前後使用區塊, 或在呼叫的方法內。

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>以新名稱儲存原生檔

1. 使用完整路徑和檔案名<xref:Microsoft.Office.Interop.Word.Document> , 呼叫您想要儲存之的方法。<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。

     下列程式碼範例會以新的名稱儲存使用中的檔。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

    > [!NOTE]
    > 如果<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>目標目錄不存在, 或如果儲存檔案時發生其他問題, 方法就會擲回例外狀況。 最好的作法是使用**try ...** 方法<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>周圍或呼叫方法內的 catch 區塊。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>編譯程式碼

這個程式碼範例需要下列項目：

- 若要依名稱儲存檔, 名為*NewDocument*的檔必須存在於磁片磁碟機 C 上名為*Test*的目錄中。

- 若要以新名稱儲存檔, 磁片磁碟機 C 上必須存在名為*Test*的目錄。

## <a name="see-also"></a>另請參閱

- [如何：以程式設計方式關閉檔](../vsto/how-to-programmatically-close-documents.md)
- [如何：以程式設計方式開啟現有檔](../vsto/how-to-programmatically-open-existing-documents.md)
- [檔主專案](../vsto/document-host-item.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
