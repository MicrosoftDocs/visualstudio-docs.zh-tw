---
title: 如何：以程式設計方式儲存檔
description: 瞭解如何使用 Visual Studio 以程式設計方式儲存檔，而不需要變更檔案名稱或新名稱。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 97f56ce0bd44eac71430a099b4fda9a7eddc7958
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107829004"
---
# <a name="how-to-programmatically-save-documents"></a>如何：以程式設計方式儲存檔

有幾種方式可以儲存 Microsoft Office Word 檔。 您可以儲存檔而不變更檔案名稱，也可以使用新名稱儲存檔。

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>儲存檔而不變更名稱

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>若要儲存與檔層級自訂相關聯的檔

1. 請呼叫 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 類別的 <xref:Microsoft.Office.Tools.Word.Document> 方法。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet7":::

### <a name="to-save-the-active-document"></a>若要儲存使用中的檔

1. 呼叫 <xref:Microsoft.Office.Interop.Word._Document.Save%2A> 現用檔的方法。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet8":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet8":::

   如果您不確定要儲存的檔是否為使用中的檔，您可以依名稱來參考它。

### <a name="to-save-a-document-specified-by-name"></a>若要儲存依名稱指定的檔

1. 使用檔案名稱做為集合的引數 <xref:Microsoft.Office.Interop.Word.Documents> 。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet9":::

## <a name="save-a-document-with-a-new-name"></a>使用新名稱儲存檔

您 `SaveAs` 可以使用方法，以新名稱儲存檔。 您可以使用 <xref:Microsoft.Office.Tools.Word.Document> 檔層級 Word 專案中的主專案方法，或 <xref:Microsoft.Office.Interop.Word.Document> 任何 Word 專案中的原生物件。 這個方法需要您指定新的檔案名，但其他引數是選擇性的。

> [!NOTE]
> 如果您在的事件處理常式內顯示 [ **SaveAs** ] 對話方塊， <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> `ThisDocument` 並將 [ *取消* ] 參數設定為 **false**，則應用程式可能會非預期地終止。 如果您將 [ *取消* ] 參數設定為 [ **true**]，就會出現錯誤訊息，指出已停用自動儲存。

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>若要使用新名稱儲存與檔層級自訂相關聯的檔

1. `SaveAs` `ThisDocument` 使用完整路徑和檔案名，在您的專案中呼叫類別的方法。 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。 若要使用這個程式碼範例，請從 `ThisDocument` 類別執行程式碼。

    > [!NOTE]
    > `SaveAs`如果目標目錄不存在或儲存檔案時發生其他問題，方法會擲回例外狀況。 最好的作法是在 `try...catch` 方法前後使用區塊， `SaveAs` 或在呼叫方法中使用區塊。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet10":::

### <a name="to-save-a-native-document-with-a-new-name"></a>使用新名稱儲存原生檔

1. <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> <xref:Microsoft.Office.Interop.Word.Document> 使用完整路徑和檔案名，呼叫您要儲存之的方法。 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。

     下列程式碼範例會以新名稱儲存使用中的檔。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

    > [!NOTE]
    > <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>如果目標目錄不存在或儲存檔案時發生其他問題，方法會擲回例外狀況。 最佳做法是使用 **try .。。** <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 方法周圍或呼叫方法內的 catch 區塊。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet10":::

## <a name="compile-the-code"></a>編譯程式碼

這段程式碼範例需要下列項目：

- 若要依名稱儲存檔，名為 *NewDocument.doc* 的檔必須存在於磁片磁碟機 C 上名為 *Test* 的目錄中。

- 若要以新名稱儲存檔，磁片磁碟機 C 上必須有名稱為 *Test* 的目錄。

## <a name="see-also"></a>另請參閱

- [如何：以程式設計方式關閉檔](../vsto/how-to-programmatically-close-documents.md)
- [如何：以程式設計方式開啟現有檔](../vsto/how-to-programmatically-open-existing-documents.md)
- [檔主專案](../vsto/document-host-item.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
