---
title: HOW TO：將 managed 程式碼擴充附加至文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f56d51817491726e6011e965bfd6d68630bb0dbf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441807"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>HOW TO：將 managed 程式碼擴充附加至文件
  您可以將自訂組件附加至現有的 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿。 文件或活頁簿可以處於任何支援的 Visual Studio 中的開發工具與 Microsoft Office 專案的檔案格式。 如需詳細資訊，請參閱 <<c0> [ 文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 若要將自訂附加至 Word 或 Excel 文件，請使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法的<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別。 因為<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別設計來在沒有安裝 Microsoft Office 的電腦上執行，您可以使用這個方法不直接相關 （例如主控台或 Windows Forms 應用程式中） 的 Microsoft Office 程式開發的方案中。

> [!NOTE]
> 自訂將無法載入程式碼預期沒有指定的文件的控制項。

 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:附加或中斷連結的 Word 文件從 VSTO 組件嗎？](http://go.microsoft.com/fwlink/?LinkId=136782).

### <a name="to-attach-managed-code-extensions-to-a-document"></a>若要將 managed 程式碼擴充附加至文件

1. 在專案中，而無須 Microsoft Office，例如主控台應用程式或 Windows Form 專案，加入的參考*Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll*和*Microsoft.VisualStudio.Tools.Applications.Runtime.dll*組件。

2. 新增下列**匯入**或是**使用**陳述式，以您的程式碼檔案頂端。

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. 呼叫靜態<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法。

     下列程式碼範例使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>多載。 這個多載會採用文件的完整路徑和<xref:System.Uri>，指定您想要附加至文件自訂的部署資訊清單的位置。 這個範例假設在 Word 文件名稱**WordDocument1.docx**是在桌面上，和部署資訊清單位於名為的資料夾**發佈**這也是在桌面上。

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. 建置專案，並執行您要附加自訂應用程式的電腦上。 電腦必須擁有 Visual Studio 2010 Tools for Office Runtime 安裝。

## <a name="see-also"></a>另請參閱
- [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [如何：從文件移除 managed 程式碼擴充功能](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [在 Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)
