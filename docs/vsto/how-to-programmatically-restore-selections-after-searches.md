---
title: 如何：以程式設計方式在搜尋後還原選取範圍
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30daa81c33070db3f9418b45b84b4acc6e243dc9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547091"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>如何：以程式設計方式在搜尋後還原選取範圍
  如果您在檔中尋找並取代文字，您可能會想要在搜尋完成之後，還原使用者的原始選取專案。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 範例程式中的程式碼會使用兩個 <xref:Microsoft.Office.Interop.Word.Range> 物件。 其中一個會儲存目前的 <xref:Microsoft.Office.Interop.Word.Selection> ，另一個則會設定要當做搜尋範圍使用的整份檔。

## <a name="to-restore-the-users-original-selection-after-a-search"></a>在搜尋後還原使用者的原始選取專案

1. 建立 <xref:Microsoft.Office.Interop.Word.Range> 檔和目前選取範圍的物件。

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. 執行搜尋和取代作業。

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. 選取 [開始] 範圍來還原使用者的原始選取專案。

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   下列範例示範完整的方法：

## <a name="example"></a>範例
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在檔中搜尋和取代文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [如何：以程式設計方式在 Word 中設定搜尋選項](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [如何：以程式設計方式對檔中找到的專案執行迴圈](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
