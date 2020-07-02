---
title: 如何：以程式設計方式在檔中檢查拼寫
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93ba9d9907135952f7408652bfb36f440d23138d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537848"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>如何：以程式設計方式在檔中檢查拼寫
  若要檢查檔中的拼寫，請使用 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 方法。 這個方法會傳回布林值，指出提供的參數是否拼寫正確。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>若要檢查拼寫並在訊息方塊中顯示結果

1. 呼叫 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 方法，並將文字範圍傳遞給它，以檢查是否有拼寫錯誤。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在檔中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
