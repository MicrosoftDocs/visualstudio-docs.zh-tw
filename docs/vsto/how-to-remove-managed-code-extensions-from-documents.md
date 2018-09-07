---
title: 如何： 移除文件從 managed 程式碼擴充
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a57384fa22e810be27969bb5164e1951dccd1bf2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671491"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>如何： 移除文件從 managed 程式碼擴充
  您可以透過程式設計方式移除自訂組件的文件或 Microsoft Office Word 或 Microsoft Office Excel 文件層級自訂一部分的活頁簿。 使用者可以開啟文件並檢視其內容，但不是會出現您的文件中加入任何自訂使用者介面 (UI)，並不會執行您的程式碼。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以使用其中一個，以便移除自訂組件`RemoveCustomization`所提供的方法[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 您使用哪一種方法，取決於您是否要移除在執行階段自訂 （亦即，這個字時自訂中執行程式碼文件或 Excel 活頁簿是開啟），或如果您想要移除已關閉的文件或文件的自訂該 i沒有安裝 Microsoft Office 安裝的伺服器上是 s。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[如何執行 do i： 附加或卸離 VSTO 組件從 Word 文件？](http://go.microsoft.com/fwlink/?LinkId=136782)。  
  
## <a name="to-remove-the-customization-assembly-at-runtime"></a>若要移除自訂組件，在執行階段  
  
1.  在您的自訂程式碼，呼叫<xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A>（針對 Word) 的方法或<xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A>（針對 Excel) 的方法。 不再需要自訂之後，才應該呼叫這個方法。  
  
     程式碼中呼叫這個方法，端視您的自訂的使用方式而定。 比方說，如果客戶使用您的自訂功能，直到他們準備好要將文件傳送給其他用戶端，只需要對文件本身 （不是自訂），您可以提供會呼叫某些 UI`RemoveCustomization`當客戶按一下它。 或者，如果您的自訂會填入資料的文件，第一次開啟時，但自訂不會提供直接存取客戶的任何其他功能時，您可以呼叫和快取盡速以您的自訂完成初始化文件。  
  
## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>若要移除已關閉的文件或在伺服器上的文件的自訂組件  
  
1.  在專案中，而無須 Microsoft Office，例如主控台應用程式或 Windows Form 專案，加入的參考*Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll*組件。  
  
2.  新增下列**匯入**或是**使用**陳述式，以您的程式碼檔案頂端。  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  呼叫靜態<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>方法的<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別，並指定解決方案的文件路徑參數。  
  
     下列程式碼範例假設您要從名為文件移除自訂*WordDocument1.docx* ，是在桌面上。  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  建置專案，並執行您要移除自訂應用程式的電腦上。 電腦必須擁有 Visual Studio 2010 Tools for Office runtime 安裝。  
  
## <a name="see-also"></a>另請參閱  
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何： 附加 Managed 程式碼加入文件的延伸模組](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  