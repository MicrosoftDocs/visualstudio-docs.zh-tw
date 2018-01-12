---
title: "如何： 以程式設計方式儲存文件 |Microsoft 文件"
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
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 68bf8450906dae3faf5f62acd2d057718938b520
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-documents"></a>如何：以程式設計方式儲存文件
  有幾種方式來儲存 Microsoft Office Word 文件。 您可以儲存文件，而不需要變更的文件的名稱，或您可以使用新名稱儲存文件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>儲存文件，而不需要變更名稱  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>若要儲存的文件層級自訂相關聯的文件  
  
1.  請呼叫 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 方法。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>若要儲存使用中文件  
  
1.  呼叫<xref:Microsoft.Office.Interop.Word._Document.Save%2A>主動式文件的方法。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 如果您不確定您想要儲存文的件是否是現用的文件，您可以用它的名稱來參考它。  
  
#### <a name="to-save-a-document-specified-by-name"></a>儲存文件名稱所指定  
  
1.  使用文件名稱做為引數<xref:Microsoft.Office.Interop.Word.Documents>集合。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>以新名稱儲存文件  
 您可以使用 另存新檔方法來以新名稱儲存文件。 您可以使用這個方法的<xref:Microsoft.Office.Tools.Word.Document>主項目，在文件層級 Word 專案中，或是原生<xref:Microsoft.Office.Interop.Word.Document>在任何 Word 專案中的物件。 這個方法需要您指定新的檔案名稱，但其他引數是選擇性的。  
  
> [!NOTE]  
>  如果您顯示**另存新檔**對話方塊內的<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>事件處理常式`ThisDocument`並設定*取消*參數**false**，應用程式可能會意外結束。 如果您設定*取消*參數**true**，出現錯誤訊息，指出 已停用自動儲存。  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>若要儲存具有新名稱的文件層級自訂相關聯的文件  
  
1.  呼叫<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>方法`ThisDocument`在專案中，使用完整的路徑和檔案名稱的類別。 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。 若要使用這個程式碼範例，請從 `ThisDocument` 類別執行程式碼。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>方法擲回例外狀況，如果目標目錄不存在，或有其他問題，儲存檔案。 它是最好的作法是使用**try … catch**封鎖周圍<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>方法或呼叫的方法內。  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>若要以新名稱儲存原生的文件  
  
1.  呼叫<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>方法<xref:Microsoft.Office.Interop.Word.Document>您想要儲存，請使用完整的路徑和檔案名稱。 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。  
  
     下列程式碼範例將使用新名稱儲存使用中文件。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>方法擲回例外狀況，如果目標目錄不存在，或有其他問題，儲存檔案。 它是最好的作法是使用**try … catch**封鎖周圍<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>方法或呼叫的方法內。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   若要依名稱儲存文件，文件名稱 NewDocument.doc 必須存在於磁碟機 c 上名為 Test 的目錄  
  
-   若要以新名稱儲存文件，名為 Test 的目錄必須存在於磁碟機 c。  
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式關閉文件](../vsto/how-to-programmatically-close-documents.md)   
 [如何： 以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Document 主項目](../vsto/document-host-item.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  