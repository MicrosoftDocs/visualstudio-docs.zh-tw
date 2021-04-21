---
title: 如何：以程式設計方式計算檔中的字元
description: 瞭解如何使用字元集合的 Count 屬性來判斷檔中的字元數。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68ddc86183eacd7f76e39bb06e47968c0129849c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823999"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>如何：以程式設計方式計算檔中的字元
  文件中的第一個字元是在字元位置 0，這表示插入點。 最後一個字元位置等於文件中的字元總數。 您可以藉由使用 <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> 集合的 <xref:Microsoft.Office.Interop.Word.Characters> 屬性來判斷文件中的字元數。

 會計算文件中的所有字元，包括空格、段落標記和其他一些通常會隱藏的字元。 即使是新的空白文件也會傳回一個字元的計數，因為其中包含一個段落標記。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>顯示文件層級自訂中的字元數

1. 選取整份文件。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet98":::

2. 在訊息方塊中顯示文件裡的字元數。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet99":::

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>顯示 VSTO 增益集中的字元數

1. 選取整份文件。 下列範例會選取使用中的文件。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet98":::

2. 在訊息方塊中顯示文件裡的字元數。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet99":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式取得範圍中的開始和結束字元](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
