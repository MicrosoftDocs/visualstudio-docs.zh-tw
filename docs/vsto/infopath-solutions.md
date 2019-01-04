---
title: InfoPath 方案
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0d346437d6d520ce3beed564c82895ef9f4d1be4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864943"
---
# <a name="infopath-solutions"></a>InfoPath 方案
  Visual Studio 提供的專案範本，可用來建立 Microsoft Office InfoPath 2013 與 InfoPath 2010 的 VSTO 增益集。 Office 2016 不提供 InfoPath。  
  
> [!NOTE]  
>  您仍然可以建立 VSTO 增益集 infopath 即使安裝了 Office 2016。 只安裝與 Office 2016 並行的 InfoPath 2013 或 Office 2013。  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  想要開發解決方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集較小的使用量，相較於 VSTO 增益集和解決方案，而且您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3、 以及 XML 來建置。  
  
 InfoPath 的 VSTO 增益集類似於其他 Microsoft Office 應用程式的 VSTO 增益集。 這類方案是由應用程式載入的組件所組成。 無論開啟何種表單或表單範本，使用者都可以存取此組件的功能。 如需 VSTO 增益集的詳細資訊，請參閱[開始 programming VSTO add-ins](../vsto/getting-started-programming-vsto-add-ins.md)並[Architecture of VSTO 增益集](../vsto/architecture-of-vsto-add-ins.md)。  
  
> [!NOTE]  
>  Visual Studio 2015 不包含舊版 Visual Studio 曾提供的 InfoPath 表單範本專案。 在舊版 Visual Studio 中建立的 InfoPath 表單範本專案，也無法使用 Visual Studio 2015 開啟或編輯。 不過，您可以使用 Visual Studio Tools for Applications 開啟和編輯 InfoPath 表單範本專案。 如需詳細資訊，請參閱[使用 VSTO 2008 專案在 InfoPath 2010 中](http://go.microsoft.com/fwlink/?LinkID=218903)。  
  
## <a name="automate-infopath-by-using-an-add-in"></a>使用增益集自動化 InfoPath  
 若要從在 Visual Studio 中使用 Office 開發工具建立的 Office VSTO 增益集存取 InfoPath 物件模型，請使用專案中 `Application` 類別的 `ThisAddIn` 欄位。 `Application` 欄位傳回的 <xref:Microsoft.Office.Interop.InfoPath.Application> 物件，代表 InfoPath 目前的執行個體。 如需詳細資訊，請參閱 <<c0> [ 程式的 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。  
  
 當您從 VSTO 增益集呼叫 InfoPath 物件模型時，您會使用 InfoPath 主要 interop 組件中所提供的類型。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與 InfoPath 中 COM 物件模型之間的橋樑。 InfoPath 主要 Interop 組件中的所有類型，都是在 <xref:Microsoft.Office.Interop.InfoPath> 命名空間中定義。 如需 InfoPath 主要 interop 組件的詳細資訊，請參閱[關於 「 Microsoft Office InfoPath 主要 interop 組件](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)。 如需主要 interop 組件的詳細資訊在一般情況下，請參閱[Office 方案開發概觀&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)並[Office 主要 interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>使用增益集自訂 InfoPath 使用者介面  
 當您針對 InfoPath 建立 VSTO 增益集時，您會有數個不同的 UI 自訂選項。 下表列出其中一些選項。  
  
|工作|如需詳細資訊|  
|----------|--------------------------|  
|建立自訂工作窗格。|[自訂工作窗格](../vsto/custom-task-panes.md)|  
|在 InfoPath 的功能區中加入自訂索引標籤。|[自訂 infopath 的功能區](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 如需有關自訂 InfoPath 的 UI 和其他 Microsoft Office 應用程式的詳細資訊，請參閱 < [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="see-also"></a>另請參閱  
 [有關 Microsoft Office InfoPath 主要 interop 組件](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [開始進行程式設計 VSTO 增益集](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)   
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 主要 interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [中的 Office 程式開發的 InfoPath 2010](http://go.microsoft.com/fwlink/?LinkId=199012)  
