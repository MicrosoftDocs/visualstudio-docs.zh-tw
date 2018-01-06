---
title: "如何： 以程式設計方式列印文件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec4808adeb38d0ee8cf13d28e181260fbbae95bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-print-documents"></a>如何：以程式設計方式列印文件
  您可以將整個 Microsoft Office Word 文件，或文件的一部分，列印到預設印表機。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="printing-a-document-that-is-part-of-a-document-level-customization"></a>印列屬於文件層級自訂一部分的文件  
  
#### <a name="to-print-the-entire-document"></a>列印整份文件  
  
1.  在專案中呼叫 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 類別的 `ThisDocument` 方法來列印整份文件。 若要使用這個範例，請從 `ThisDocument` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
#### <a name="to-print-the-current-page-of-the-document"></a>列印文件的目前頁面  
  
1.  在專案中呼叫 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 類別的 `ThisDocument` 方法，並指定要列印一份目前的頁面。 若要使用這個範例，請從 `ThisDocument` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="printing-a-document-by-using-an-vsto-add-in"></a>使用 VSTO 增益集來列印文件  
  
#### <a name="to-print-an-entire-document"></a>列印整份文件  
  
1.  呼叫您要列印之 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Document> 方法。 下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
#### <a name="to-print-the-current-page-of-a-document"></a>列印文件的目前頁面  
  
1.  呼叫您要列印之 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Document> 方法，並指定要列印一份目前的頁面。 下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>請參閱  
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  