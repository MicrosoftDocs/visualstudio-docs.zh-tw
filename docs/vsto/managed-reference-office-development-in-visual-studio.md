---
title: Managed 參考 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b0b6d7b6fdbb55030088f33fc235429d0b6142e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Managed 參考 (Visual Studio 中的 Office 程式開發)
  本節包含命名空間的應用程式開發介面參考文件，和用在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]之 Office 專案中的類型。 如需命名空間和類型，在.NET Framework 3.5 為目標的 Office 專案中可用的 API 參考文件，請參閱 Visual Studio 文件中的下列參考章節： [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658)。  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
## <a name="in-this-section"></a>本節內容  
 <xref:Microsoft.Office.Tools>  
 包含程式設計 Office 解決方案的常見類別。 包括 VSTO 增益集的基底類別、在 VSTO 增益集中建立自訂工作窗格的類別、在 Excel 和 Word 解決方案中建立智慧標籤的類別，以及在文件層級自訂中建立執行窗格的類別。  
  
 <xref:Microsoft.Office.Tools.Excel>  
 包含可用於 Excel 解決方案的主控制項和主項目。  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 包含可用於 Excel 解決方案的 Excel 控制項和 Windows Form 控制項。  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 包含 Outlook VSTO 增益集使用的類別，包括用來建立自訂表單區域的類別。  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 包含用於以程式設計方式修改功能區自訂項目的類別，這些功能區自訂項目是使用功能區設計工具所建立。  
  
 <xref:Microsoft.Office.Tools.Word>  
 包含可用於 Word 解決方案的主控制項和主項目。  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 包含可用於 Word 解決方案的 Word 控制項和 Windows Forms 控制項。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 包含 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別和一組相關的快取資料類別。 在沒有安裝 Microsoft Office 的電腦上，這些類別可以用來修改文件層級自訂的某些層面。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 包含 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 介面 (可實作來建立 Office 解決方案的 *部署後動作* )、在安裝 Office 解決方案時可能會擲回的例外狀況，以及其他屬於 Visual Studio 基礎結構的應用程式開發介面。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 包含可由 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]擲回的大部分例外狀況，可以用來快取文件層級自訂項目資料的數種類別，以及其他屬於 Visual Studio 基礎結構的應用程式開發介面。  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 包含用於建置 Office 專案的 MSBuild 工作類別。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [使用者入門&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  