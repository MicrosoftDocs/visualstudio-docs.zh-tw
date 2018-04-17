---
title: 如何： 以程式設計方式在 Word 中設定搜尋選項 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3be8d12f18e4ea0b6d05cbad92c08c7b5427315c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>如何：以程式設計方式在 Word 中設定搜尋選項
  有兩種方式可在 Microsoft Office Word 文件中設定搜尋選項的選取項目：  
  
-   設定個別屬性<xref:Microsoft.Office.Interop.Word.Find>物件。  
  
-   使用引數的<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>方法<xref:Microsoft.Office.Interop.Word.Find>物件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>使用尋找物件的屬性  
 下列程式碼中設定的屬性<xref:Microsoft.Office.Interop.Word.Find>物件目前的選取範圍內搜尋文字。 請注意，搜尋條件，例如搜尋順向、 換行和搜尋的文字內容的<xref:Microsoft.Office.Interop.Word.Find>物件。  
  
 設定每個屬性的<xref:Microsoft.Office.Interop.Word.Find>物件不實用，當您撰寫 C# 程式碼，因為您必須指定相同的屬性中當做參數<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>方法。 因此這個範例包含只有 Visual Basic 程式碼。  
  
#### <a name="to-set-search-options-using-a-find-object"></a>若要設定使用尋找物件的搜尋選項  
  
1.  設定的屬性<xref:Microsoft.Office.Interop.Word.Find>來搜尋文字選取範圍的物件**找到我**。  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>使用 Execute 方法引數  
 下列程式碼會使用<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>方法<xref:Microsoft.Office.Interop.Word.Find>物件目前的選取範圍內搜尋文字。 請注意，搜尋條件，例如搜尋順向、 換行和搜尋的文字會當做參數傳遞<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>方法。  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>若要設定使用 Execute 方法引數的搜尋選項  
  
1.  傳遞做為參數的搜尋準則<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>方法來搜尋文字選取範圍**找到我**。  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式搜尋和取代文件中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [如何： 以程式設計方式重複使用文件中找到的項目](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [如何：以程式設計方式在搜尋後還原選取範圍](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  