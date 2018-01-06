---
title: "如何： 以程式設計方式列印 Visio 文件 |Microsoft 文件"
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
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
ms.assetid: 606a2678-5eb8-40b2-a50a-305cecb1b3d4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b07e0534c7ada907fb3140270087dcd5b048621
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-print-visio-documents"></a>如何：以程式設計方式列印 Visio 文件
  您可以列印整份 Microsoft Office Visio 文件，或僅列印特定頁面。  
  
 如需此列印方法的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) 方法和 [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) 方法的 VBA 參考文件。  
  
## <a name="printing-a-visio-document"></a>列印 Visio 文件  
  
#### <a name="to-print-a-complete-document"></a>列印整份文件  
  
-   呼叫您要列印的 Microsoft.Office.Interop.Visio.Document 物件 Microsoft.Office.Interop.Visio.Document.Print 方法。  
  
     下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>列印 Visio 文件頁面  
  
#### <a name="to-print-a-page-of-a-document"></a>列印文件頁面  
  
-   呼叫您要列印的 Microsoft.Office.Interop.Visio.Pages 物件 Microsoft.Office.Interop.Visio.Pages.Print 方法。  
  
     下列程式碼範例會列印使用中之文件的第一頁。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何： 以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  