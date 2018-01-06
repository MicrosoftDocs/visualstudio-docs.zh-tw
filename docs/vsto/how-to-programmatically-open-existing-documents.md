---
title: "如何： 以程式設計方式開啟現有文件 |Microsoft 文件"
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 991a282cb3fc8a34f3434c9cdb0a9be214c9e3bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-existing-documents"></a>如何：以程式設計方式開啟現有文件
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法會開啟完整的路徑和檔案名稱所指定的現有 Microsoft Office Word 文件。 這個方法會傳回<xref:Microsoft.Office.Interop.Word.Document>表示開啟的文件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>若要開啟的文件  
  
-   呼叫<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法<xref:Microsoft.Office.Interop.Word.Documents>集合，並提供文件的路徑。  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>若要開啟的文件為唯讀  
  
-   呼叫<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法，提供文件的路徑，以及設定*ReadOnly*引數**True**方法呼叫中。  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   名為 NewDocument.doc 文件必須位於 c 磁碟機上名為測試目錄  
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)   
 [如何： 以程式設計方式關閉文件](../vsto/how-to-programmatically-close-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  