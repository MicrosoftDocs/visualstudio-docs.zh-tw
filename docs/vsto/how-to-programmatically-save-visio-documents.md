---
title: "如何： 以程式設計方式儲存 Visio 文件 |Microsoft 文件"
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
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 946bb38d5cb79506e54206060686eac5dfc7b566
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-save-visio-documents"></a>如何：以程式設計方式儲存 Visio 文件
  儲存 Microsoft Office Visio 文件的方式有很多種：  
  
-   在現有的文件中儲存變更。  
  
-   儲存新的文件，或以新名稱儲存文件。  
  
-   以指定的引數儲存文件。  
  
 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) 方法、 [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) 方法和 [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) 方法的 VBA 參考文件。  
  
## <a name="saving-an-existing-document"></a>儲存現有的文件  
  
#### <a name="to-save-a-document"></a>儲存文件  
  
-   呼叫 Microsoft.Office.Interop.Visio.Document.Save 方法 Microsoft.Office.Tools.Visio.Document 類別的已儲存的文件。  
  
     若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
    > [!NOTE]  
    >  如果尚未儲存新的 Visio 文件 Microsoft.Office.Interop.Visio.Document.Save 方法會擲回例外狀況。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>以新名稱儲存文件  
 您可以使用 Microsoft.Office.Interop.Visio.Document.SaveAs 方法來儲存新的文件或具有新名稱的文件。 這個方法需要指定新的檔案名稱。  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>以新名稱儲存使用中的 Visio 文件  
  
-   呼叫您要使用包括檔案名稱的完整的路徑來儲存 Microsoft.Office.Tools.Visio.Document Microsoft.Office.Interop.Visio.Document.SaveAs 方法。 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。  
  
     若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>以新名稱和指定的引數儲存文件  
 具有新名稱儲存文件使用 Microsoft.Office.Interop.Visio.Document.SaveAsEx 方法並指定任何適用的引數套用至文件。  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>以新名稱和指定的引數儲存文件  
  
-   呼叫您要使用包括檔案名稱的完整的路徑來儲存 Microsoft.Office.Tools.Visio.Document Microsoft.Office.Interop.Visio.Document.SaveAsEx 方法。 如果該資料夾中已有同名的檔案，即擲回例外狀況。  
  
     下列程式碼範例會以新名稱儲存使用中的文件、將文件標示為唯讀，以及在 [最近使用的清單] 中顯示文件。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   若要儲存具有新名稱的文件，[我的文件] 資料夾 (Windows XP 及更早版本) 或 [文件] 資料夾 (Windows Vista) 中必須要有名為 `Test` 的目錄。  
  
## <a name="see-also"></a>請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何： 以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  