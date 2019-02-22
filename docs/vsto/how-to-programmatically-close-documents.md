---
title: HOW TO：以程式設計方式關閉文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd5e73a272243aeb2ddc38ea5c2f49bb1b62e6a0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598358"
---
# <a name="how-to-programmatically-close-documents"></a>HOW TO：以程式設計方式關閉文件
  您可以關閉使用中文件，或者指定要關閉的文件。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>關閉使用中的文件
 有兩種程序可以關閉使用中文件：一個適用於文件層級自訂，而另一個適用於 VSTO 增益集。

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>關閉文件層級自訂中的使用中文件

1.  呼叫專案中 <xref:Microsoft.Office.Tools.Word.Document.Close%2A> 類別的 `ThisDocument` 方法，關閉與自訂相關聯的文件。 若要使用下列程式碼範例，請從 `ThisDocument` 類別執行程式碼。

    > [!NOTE]
    >  這個範例會將 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值傳遞給 *SaveChanges* 參數，關閉但不儲存變更或提示使用者。

     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>關閉 VSTO 增益集中的使用中文件

1.  呼叫 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 屬性的 <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> 方法，關閉使用中的文件。 若要使用下列程式碼範例，請從專案的 `ThisAddIn` 類別中執行此範例。

    > [!NOTE]
    >  這個範例會將 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值傳遞給 *SaveChanges* 參數，關閉但不儲存變更或提示使用者。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]

## <a name="close-a-document-that-you-specify-by-name"></a>關閉您依名稱指定的文件
 對 VSTO 增益集和文件層級自訂而言，依指定名稱關閉文件的方式都是相同的。

### <a name="to-close-a-document-that-you-specify-by-name"></a>依指定名稱關閉文件

1.  指定文件名稱為 <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> 集合的引數，然後再呼叫 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 方法。 下列程式碼範例假設在 Word 中開啟了名為 **NewDocument** 的文件。

    > [!NOTE]
    >  這個範例會將 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值傳遞給 *SaveChanges* 參數，關閉但不儲存變更或提示使用者。

     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)
- [如何：以程式設計方式儲存文件](../vsto/how-to-programmatically-save-documents.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
