---
title: HOW TO：以程式設計方式檢查文件中的拼字
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 26eb7e0798fbcf6aad33dd45892a23fb0d54b812
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110085"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>HOW TO：以程式設計方式檢查文件中的拼字
  若要檢查文件中的拼字錯誤，請使用<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>方法。 這個方法會傳回布林值，指出所提供的參數的拼字是否正確。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>若要檢查拼字，並在訊息方塊中顯示結果

1. 呼叫<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>方法並將它傳遞來檢查是否有拼字錯誤的文字範圍。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式定義，並在文件中選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
