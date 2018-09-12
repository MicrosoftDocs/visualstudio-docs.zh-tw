---
title: 如何： 以程式設計方式儲存 Visio 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4171f0237b7735748da567bd9482856c013759bc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671485"
---
# <a name="how-to-programmatically-save-visio-documents"></a>如何： 以程式設計方式儲存 Visio 文件
  儲存 Microsoft Office Visio 文件的方式有很多種：  
  
-   在現有的文件中儲存變更。  
  
-   儲存新的文件，或以新名稱儲存文件。  
  
-   以指定的引數儲存文件。  
  
 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) 方法、 [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) 方法和 [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) 方法的 VBA 參考文件。  
  
## <a name="save-an-existing-document"></a>儲存現有的文件  
  
### <a name="to-save-a-document"></a>儲存文件  
  
-   呼叫`Microsoft.Office.Interop.Visio.Document.Save`方法的`Microsoft.Office.Tools.Visio.Document`已儲存過文件的類別。  
  
     若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
    > [!NOTE]  
    >  `Microsoft.Office.Interop.Visio.Document.Save`方法擲回例外狀況，如果尚未儲存新的 Visio 文件。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>使用新名稱儲存文件  
 使用`Microsoft.Office.Interop.Visio.Document.SaveAs`方法來儲存新的文件或具有新名稱的文件。 這個方法需要指定新的檔案名稱。  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>以新名稱儲存使用中的 Visio 文件  
  
-   呼叫`Microsoft.Office.Interop.Visio.Document.SaveAs`方法的`Microsoft.Office.Tools.Visio.Document`您想要儲存，請使用完整的路徑，包括檔案名稱。 如果該資料夾中已有同名的檔案，即會以無訊息方式覆寫。  
  
     若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>使用新的名稱和指定的引數儲存文件  
 使用`Microsoft.Office.Interop.Visio.Document.SaveAsEx`具有新名稱儲存文件，並指定任何適用的引數套用至文件的方法。  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>以新名稱和指定的引數儲存文件  
  
-   呼叫`Microsoft.Office.Interop.Visio.Document.SaveAsEx`方法的`Microsoft.Office.Tools.Visio.Document`您想要儲存，請使用完整的路徑，包括檔案名稱。 如果該資料夾中已有同名的檔案，即擲回例外狀況。  
  
     下列程式碼範例會以新名稱儲存使用中的文件、將文件標示為唯讀，以及在 [最近使用的清單] 中顯示文件。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   若要儲存具有新名稱的文件，目錄名稱為`Test`必須位於*我的文件*資料夾 （適用於 Windows XP 及更早版本） 或*文件*（適用於 Windows Vista) 的資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何： 以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何： 以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  