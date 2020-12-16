---
title: 如何：以程式設計方式在 Word 中設定搜尋選項
description: 瞭解如何使用 Visual Studio，以程式設計方式為 Microsoft Word 中的選取專案設定搜尋選項。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45af6a801a146838919402c31be502cf4825e718
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528561"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>如何：以程式設計方式在 Word 中設定搜尋選項
  有兩種方式可以在 Microsoft Office Word 檔中設定選項的搜尋選項：

- 設定物件的個別屬性 <xref:Microsoft.Office.Interop.Word.Find> 。

- 使用物件之方法的引數 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> <xref:Microsoft.Office.Interop.Word.Find> 。

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>使用尋找物件的屬性
 下列程式碼會設定物件的屬性 <xref:Microsoft.Office.Interop.Word.Find> ，以搜尋目前選取範圍內的文字。 請注意，搜尋條件（例如搜尋向前、換行和要搜尋的文字）是物件的屬性 <xref:Microsoft.Office.Interop.Word.Find> 。

 <xref:Microsoft.Office.Interop.Word.Find>當您撰寫 c # 程式碼時，設定物件的每個屬性並不實用，因為您必須將相同的屬性指定為方法中的參數 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 。 因此，此範例只包含 Visual Basic 程式碼。

### <a name="to-set-search-options-using-a-find-object"></a>使用尋找物件設定搜尋選項

1. 設定物件的屬性 <xref:Microsoft.Office.Interop.Word.Find> ，以便在 [ **尋找我** 的文字] 的選取範圍內向前搜尋。

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>使用 Execute 方法引數
 下列程式碼會使用 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 物件的方法 <xref:Microsoft.Office.Interop.Word.Find> 來搜尋目前選取範圍內的文字。 請注意，搜尋條件（例如搜尋向前、換行和要搜尋的文字）會做為方法的參數傳遞 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 。

### <a name="to-set-search-options-using-execute-method-arguments"></a>使用 Execute 方法引數設定搜尋選項

1. 將搜尋準則傳遞為方法的參數 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> ，以便向前搜尋文字 **尋找** 的選項。

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式搜尋和取代檔中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [如何：以程式設計方式在檔中找到的專案之間執行迴圈](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [如何：以程式設計方式在搜尋後還原選取專案](../vsto/how-to-programmatically-restore-selections-after-searches.md)
