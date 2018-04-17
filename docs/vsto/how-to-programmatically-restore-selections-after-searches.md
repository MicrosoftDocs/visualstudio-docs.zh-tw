---
title: 如何： 以程式設計方式搜尋後還原選取 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d1f4181a1ce9431ecbdb69a4b4f00a70f8259d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>如何：以程式設計方式在搜尋後還原選取
  如果您尋找和取代文件中的文字，您可能要完成搜尋之後還原使用者的原始選取項目。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 此範例程序中的程式碼會使用兩個<xref:Microsoft.Office.Interop.Word.Range>物件。 其中一個存放區目前<xref:Microsoft.Office.Interop.Word.Selection>，和其中一個設定要做為搜尋範圍將整個文件。  
  
### <a name="to-restore-the-users-original-selection-after-a-search"></a>若要還原的使用者在搜尋之後的原始選取項目  
  
1.  建立<xref:Microsoft.Office.Interop.Word.Range>文件和目前的選取範圍的物件。  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  執行搜尋和取代作業。  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  選取要還原使用者的原始選取項目開始範圍。  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 下列範例示範完整的方法：  
  
## <a name="example"></a>範例  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式搜尋和取代文件中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [如何： 以程式設計方式在 Word 中設定搜尋選項](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [如何： 以程式設計方式重複使用文件中找到的項目](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  