---
title: "如何： 從文件移除 Managed 程式碼擴充 |Microsoft 文件"
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
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9da75468ae417bd835b457cdbd5219ef9462df1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>如何：從文件移除 Managed 程式碼擴充
  您可以透過程式設計方式移除自訂組件的文件或 Microsoft Office Word 或 Microsoft Office Excel 文件層級自訂一部分的活頁簿。 使用者可以開啟文件並檢視其內容，但是不會出現您加入文件任何自訂使用者介面 (UI)，而且將不會執行您的程式碼。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以使用其中一種和快取所提供的方法來移除自訂組件[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 您使用的方法取決於您是否想要移除自訂執行階段 （也就是這個字時自訂中執行程式碼文件或 Excel 活頁簿已展開），或如果您想要移除已關閉的文件或文件的自訂 is 並沒有安裝 Microsoft Office 的伺服器上。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何執行 i： 附加或卸離 VSTO 組件從 Word 文件？](http://go.microsoft.com/fwlink/?LinkId=136782)。  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>若要移除自訂組件，在執行階段  
  
1.  在您的自訂程式碼，呼叫<xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A>（適用於 Word) 的方法或<xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A>（針對 Excel) 的方法。 不再需要自訂之後，才應該呼叫這個方法。  
  
     程式碼中呼叫這個方法，取決於您的自訂的使用方式。 例如，如果客戶使用您的自訂功能，直到他們就可以將文件傳送至其他用戶端只需要在文件本身 （不是自訂），您可以提供呼叫和快取，當客戶按一下它時一些 UI。 或者，如果第一次開啟時，但自訂不會提供直接存取客戶的其他任何功能時，您的自訂會填入資料的文件，然後您可以呼叫和快取項目一旦您的自訂完成初始化文件。  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>若要移除已關閉的文件或文件的伺服器上的自訂組件  
  
1.  在不需要 Microsoft Office，例如主控台應用程式的專案或 Windows Form 專案中，加入 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 組件的參考。  
  
2.  加入下列**匯入**或**使用**陳述式加入您的程式碼檔案頂端。  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  呼叫靜態<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>方法<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別，並指定參數的方案文件路徑。  
  
     下列程式碼範例假設您要從名為文件移除自訂**WordDocument1.docx** ，會在桌面上。  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  建置專案，並執行您要移除自訂應用程式的電腦上。 電腦必須有 Visual Studio 2010 Tools for Office Runtime 安裝。  
  
## <a name="see-also"></a>另請參閱  
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何：將 Managed 程式碼擴充附加至文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  