---
title: 如何：將 managed 程式碼擴充附加至檔
description: 瞭解如何將自訂群組件附加至現有的 Microsoft Office Word 檔或 Microsoft Office Excel 活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 063b66af781ee412e7f7d2ab8014e009bc93bad9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954107"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>如何：將 managed 程式碼擴充附加至檔
  您可以將自訂群組件附加至現有的 Microsoft Office Word 檔或 Microsoft Office Excel 活頁簿。 檔或活頁簿可以使用 Visual Studio 中的 Microsoft Office 專案和開發工具所支援的任何檔案格式。 如需詳細資訊，請參閱 [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 若要將自訂附加至 Word 或 Excel 檔，請使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 類別的方法 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 。 因為 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別是設計為在未安裝 Microsoft Office 的電腦上執行，所以您可以在與 Microsoft Office 開發 (（例如主控台或 Windows Forms 應用程式) ）無關的解決方案中使用這個方法。

> [!NOTE]
> 如果程式碼需要指定檔沒有的控制項，自訂將無法載入。

### <a name="to-attach-managed-code-extensions-to-a-document"></a>將 managed 程式碼擴充附加至檔

1. 在不需要 Microsoft Office 的專案中（例如主控台應用程式或 Windows Forms 專案），加入 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* 和 *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* 元件的參考。

2. 將下列 **Imports** 或 **using** 語句新增至程式碼檔案的頂端。

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. 呼叫靜態 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。

     下列程式碼範例會使用多載 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 。 這個多載會採用檔的完整路徑，以及 <xref:System.Uri> 指定您要附加至檔之自訂的部署資訊清單位置。 此範例假設名為 **WordDocument1.docx** 的 Word 檔位於桌面上，而且部署資訊清單位於名為 **Publish** 且位於桌面上的資料夾中。

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. 在您要附加自訂的電腦上建立專案，並執行應用程式。 電腦必須安裝 Visual Studio 2010 Tools for Office Runtime。

## <a name="see-also"></a>另請參閱
- [使用 ServerDocument 類別管理伺服器上的檔](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [如何：從檔中移除 managed 程式碼延伸模組](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)
