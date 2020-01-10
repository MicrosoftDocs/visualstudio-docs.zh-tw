---
title: 如何：將 managed 程式碼擴充附加至檔
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
ms.openlocfilehash: 8fb212f9c5441d697cfa92feee7dc18fab9270d2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985969"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>如何：將 managed 程式碼擴充附加至檔
  您可以將自訂群組件附加至現有的 Microsoft Office Word 檔或 Microsoft Office Excel 活頁簿。 檔或活頁簿可以是 Visual Studio 中 Microsoft Office 專案和開發工具支援的任何檔案格式。 如需詳細資訊，請參閱[檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 若要將自訂附加至 Word 或 Excel 檔，請使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。 因為 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別是設計用來在未安裝 Microsoft Office 的電腦上執行，所以您可以在與 Microsoft Office 開發無關的方案（例如主控台或 Windows Forms 應用程式）中使用此方法。

> [!NOTE]
> 如果程式碼需要指定檔沒有的控制項，則自訂將無法載入。

### <a name="to-attach-managed-code-extensions-to-a-document"></a>將 managed 程式碼擴充附加至檔

1. 在不需要 Microsoft Office （例如主控台應用程式或 Windows Forms 專案）的專案中，新增 VisualStudio 的參考，並*ServerDocument* *VisualStudio：應用程式的執行時間 .dll*元件。

2. 在程式碼檔案的頂端新增下列**Imports**或**using**語句。

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. 呼叫靜態 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。

     下列程式碼範例會使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 多載。 這個多載會採用檔的完整路徑，以及指定您想要附加至檔之自訂的部署資訊清單位置的 <xref:System.Uri>。 這個範例假設名為**worddocument1.docx**的 Word 檔位於桌面上，而且部署資訊清單位於名為**Publish**的資料夾中，也是在桌面上。

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. 建立專案，然後在您要附加自訂的電腦上執行應用程式。 電腦必須安裝適用于 Office Runtime 的 Visual Studio 2010 工具。

## <a name="see-also"></a>請參閱
- [使用 ServerDocument 類別管理伺服器上的檔](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [如何：從檔移除 managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)
