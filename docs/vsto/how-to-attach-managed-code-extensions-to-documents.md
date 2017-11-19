---
title: "如何： 將 Managed 程式碼擴充附加至文件 |Microsoft 文件"
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
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3f5703b54a1deb96e9d6719c2726164e1002a18f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>如何：將 Managed 程式碼擴充附加至文件
  您可以將自訂組件附加至現有的 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿。 文件或活頁簿可以處於任何支援的 Microsoft Office 專案和 Visual Studio 中的開發工具的檔案格式。 如需詳細資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 若要附加自訂 Word 或 Excel 的文件，使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別。 因為<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別設計來在沒有安裝 Microsoft Office 的電腦上執行，您可以使用這個方法中 Microsoft Office 程式開發 （例如主控台或 Windows Forms 應用程式中） 沒有直接相關的解決方案。  
  
> [!NOTE]  
>  自訂將無法載入如果程式碼必須有沒有指定的文件的控制項。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何執行 i： 附加或卸離 VSTO 組件從 Word 文件？](http://go.microsoft.com/fwlink/?LinkId=136782)。  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>若要將 managed 程式碼擴充附加至文件  
  
1.  在專案中，不需要 Microsoft Office，例如主控台應用程式或 Windows Form 專案，將參考加入 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 和 Microsoft.VisualStudio.Tools.Applications.Runtime.dll組件。  
  
2.  加入下列**匯入**或**使用**陳述式加入您的程式碼檔案頂端。  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  呼叫靜態<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法。  
  
     下列程式碼範例使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>多載。 這個多載會採用文件的完整路徑和<xref:System.Uri>可指定您想要附加至文件的自訂部署資訊清單的位置。 這個範例假設在 Word 文件名為**WordDocument1.docx**是在桌面上，和部署資訊清單位於名為的資料夾中**發行**其同時也是在桌面上。  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  建置專案，並執行您要附加自訂應用程式的電腦上。 電腦必須有 Visual Studio 2010 Tools for Office Runtime 安裝。  
  
## <a name="see-also"></a>另請參閱  
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何： 從文件移除 Managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  