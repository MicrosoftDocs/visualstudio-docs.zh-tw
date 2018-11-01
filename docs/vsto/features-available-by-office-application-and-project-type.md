---
title: 依 Office 應用程式和專案類型提供的功能
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fac14df471b0dfcda1d0bf4763158280211bc33
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672443"
---
# <a name="features-available-by-office-application-and-project-type"></a>依 Office 應用程式和專案類型提供的功能
  Visual Studio 有幾種類型的專案範本，可支援不同的 Microsoft Office 應用程式商務案例，包括下列類型：  
  
- 文件層級自訂。  
  
- VSTO 增益集。  
  
  並非所有應用程式都可以使用每個專案類型。 例如，文件層級專案僅用於 Microsoft Office Word 和 Microsoft Office Excel。 同樣地，某些功能僅用於特定類型的專案或應用程式。 例如，執行窗格只用於文件層級專案，而功能區擴充功能只用於某些應用程式。 如需不同專案類型的詳細資訊，請參閱[Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
> [!NOTE]  
>  Office 專案範本只用於某些版本的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>適用於不同的 Microsoft Office 應用程式的專案類型  
 下表顯示您可以搭配每個專案類型使用的應用程式。  
  
|專案類型|Microsoft Office 應用程式|  
|-------------------|----------------------------------|  
|文件層級自訂|Excel<br /><br /> 字組|  
|VSTO 增益集|Excel<br /><br /> InfoPath (僅限 InfoPath 2013 與 InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> 專案<br /><br /> Visio<br /><br /> 字組<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>在不同的專案類型提供的功能  
 下表顯示哪些專案類型提供各項功能。  
  
|功能|提供功能的專案類型|進一步閱讀|  
|-------------|--------------------------------------------|---------------------|  
|執行窗格。|文件層級專案。|[執行窗格概觀](../vsto/actions-pane-overview.md)|  
|ClickOnce 佈署。|VS 與文件層級專案。|[部署 Office 方案](../vsto/deploying-an-office-solution.md)|  
|自訂工作窗格。|下列應用程式的 VSTO 增益集專案：<br /><br /> Excel<br />-InfoPath (InfoPath 2013 與 InfoPath 2010 只）<br />-Outlook<br />-PowerPoint<br />字組|[自訂工作窗格](../vsto/custom-task-panes.md)|  
|自訂 XML 組件。|文件層級專案。<br /><br /> 下列應用程式的應用程式層級專案：<br /><br /> Excel<br />-PowerPoint<br />字組|[自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)|  
|資料快取。|文件層級專案。|[文件層級自訂中的快取的資料](../vsto/cached-data-in-document-level-customizations.md)|  
|公開的 VSTO 增益集至其他 Microsoft Office 方案中的物件。|VSTO 增益集專案。|[從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|下列主控制項：<br /><br /> -圖表<br />-ListObject<br />-NamedRange<br />-內容控制項<br />-書籤|文件層級專案。<br /><br /> Word 和 Excel 的 VSTO 增益集專案。|[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)|  
|下列主控制項：<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|文件層級專案。|[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)|  
|多專案部署。|文件層級專案。<br /><br /> VSTO 增益集專案。|[逐步解說： 部署單一的 ClickOnce 安裝程式中的多個 Office 方案](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|  
|Outlook 表單區域。|Outlook 的 VSTO 增益集專案。|[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)|  
|部署後動作。|文件層級專案。<br /><br /> VSTO 增益集專案。|[逐步解說： 在 ClickOnce 安裝之後將文件複製到終端使用者電腦](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|功能區自訂。|文件層級專案。<br /><br /> 下列應用程式的 VSTO 增益集專案：<br /><br /> Excel<br />-InfoPath (InfoPath 2013 與 InfoPath 2010 只）<br />-Outlook<br />-PowerPoint<br />專案<br />-Visio<br />字組|[功能區概觀](../vsto/ribbon-overview.md)|  
|視覺文件設計工具。|文件層級專案。|[在 Visual Studio 環境中的 office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>另請參閱  
 [開始使用&#40;在 Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [文件層級自訂中的快取的資料](../vsto/cached-data-in-document-level-customizations.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  