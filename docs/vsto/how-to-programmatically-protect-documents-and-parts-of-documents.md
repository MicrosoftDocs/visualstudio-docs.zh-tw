---
title: HOW TO：以程式設計方式保護文件和文件的部分
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d72f7c0136921592c8327dc0c101acd63388631
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872569"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>HOW TO：以程式設計方式保護文件和文件的部分
  您可以在 Microsoft Office Word 文件加入保護，以防止使用者對文件進行任何編輯。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 您也可以將文件的特定區域標記為例外狀況，讓指定的使用者只能編輯文件的那些區域。 例如，您可能想要保護除了特定書籤以外的整份文件。 您可以選擇性地加入密碼，除非使用者知道密碼，否則無法移除文件保護。  
  
> [!NOTE]  
>  下列範例不會使用密碼保護。不過，您可以考慮在加入文件保護時使用密碼。 如需詳細資訊，請參閱文件保護裝置範例[Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
 您也可以使用內容控制項保護文件的部分。 如需詳細資訊，請參閱[＜How to：使用內容控制項保護文件的部分](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)。  
  
## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>保護文件層級自訂一部分的文件  
  
### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>保護屬於文件層級自訂一部分的文件  
  
1.  呼叫您專案中之 <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> 類別的 `ThisDocument` 方法。  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>從文件保護排除書籤控制項  
  
1.  使用 <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> 方法保護整份文件。  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  從文件保護排除 `Bookmark1` 。  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compile-the-code"></a>編譯程式碼  
 若要使用這些程式碼範例，請從專案的 `ThisDocument` 類別中執行它們。 這些程式碼範例假設您在這段程式碼出現的文件中，已有現有的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項，名為 `Bookmark1` 。  
  
## <a name="protect-a-document-by-using-a-vsto-add-in"></a>使用 VSTO 增益集來保護文件  
  
### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>使用應用程式層級 VSTO 增益集來保護文件  
  
1.  呼叫您要保護之 <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> 的 <xref:Microsoft.Office.Interop.Word.Document> 方法。  
  
     下列程式碼範例會保護使用中文件。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>另請參閱  
 [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [如何：允許程式碼的文件背後執行以限制權限](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [如何：將書籤控制項加入 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
