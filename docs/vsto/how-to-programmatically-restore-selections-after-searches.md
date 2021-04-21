---
title: 如何：以程式設計方式在搜尋後還原選取專案
description: 瞭解如何在 Microsoft Word 檔中搜尋之後，使用 Visual Studio 以程式設計方式還原選項。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a9f804e218ec9dfa0e0550501dec0c1aa8388ff
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824008"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>如何：以程式設計方式在搜尋後還原選取專案
  如果您找到並取代檔中的文字，您可能會想要在搜尋完成後還原使用者的原始選取範圍。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 範例程式中的程式碼會使用兩個 <xref:Microsoft.Office.Interop.Word.Range> 物件。 其中一個會儲存目前的 <xref:Microsoft.Office.Interop.Word.Selection> ，另一個則會將整個檔設定為搜尋範圍。

## <a name="to-restore-the-users-original-selection-after-a-search"></a>在搜尋之後還原使用者的原始選取範圍

1. 建立 <xref:Microsoft.Office.Interop.Word.Range> 檔的物件和目前的選取專案。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. 執行搜尋和取代操作。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. 選取 [開始] 範圍來還原使用者的原始選取專案。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   下列範例示範完整的方法：

## <a name="example"></a>範例
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式搜尋和取代檔中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [如何：以程式設計方式在 Word 中設定搜尋選項](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [如何：以程式設計方式在檔中找到的專案之間執行迴圈](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
