---
title: 如何： 以程式設計方式檢查拼字的文件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7445b48dc936bf57a5c93426e9ffcc7f114eb32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>如何：以程式設計方式在文件中檢查拼字
  若要檢查拼字的文件中，使用<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>方法。 這個方法會傳回布林值，指出是否將提供的參數拼寫正確。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>若要檢查拼字，並在訊息方塊中顯示結果  
  
1.  呼叫<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>方法並傳遞要檢查拼字錯誤的文字範圍。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式定義及選取範圍中的文件](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  