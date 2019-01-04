---
title: PowerPoint 方案
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0f264cd7382ea16a7c4cfa5896241f4359b0cd67
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906042"
---
# <a name="powerpoint-solutions"></a>PowerPoint 方案
  Visual Studio 提供您可用來建立 Microsoft Office PowerPoint VSTO 增益集的專案範本。 您可以使用 VSTO 增益集來自動化 PowerPoint、擴充 PowerPoint 功能，或自訂 PowerPoint 使用者介面 (UI)。  
  
 如需 VSTO 增益集的詳細資訊，請參閱[開始 programming VSTO add-ins](../vsto/getting-started-programming-vsto-add-ins.md)並[Architecture of VSTO 增益集](../vsto/architecture-of-vsto-add-ins.md)。如果您是使用 Microsoft Office 程式設計的新手，請參閱[開始&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  想要開發解決方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集較小的使用量，相較於 VSTO 增益集和解決方案，而且您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3、 以及 XML 來建置。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:建立 Microsoft PowerPoint 增益集嗎？](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>使用 PowerPoint 物件模型自動化 PowerPoint  
 PowerPoint 物件模型會公開您可用來自動化 PowerPoint 的許多類型。 這些類型可讓您撰寫程式碼來完成一般工作：  
  
- 以程式設計方式建立和格式化簡報。  
  
- 新增或移除簡報中的投影片。  
  
- 新增或變更投影片上的圖案。  
  
  若要從 VSTO 增益集存取 PowerPoint 物件模型，請使用`Application`欄位`ThisAddIn`專案中的類別。 `Application` 欄位傳回的 <xref:Microsoft.Office.Interop.PowerPoint.Application> 物件代表目前的 PowerPoint 執行個體。 如需詳細資訊，請參閱 <<c0> [ 程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。  
  
  呼叫 PowerPoint 物件模型時，您使用的類型是由 PowerPoint 的主要 Interop 組件所提供。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與 PowerPoint 中 COM 物件模型之間的橋樑。 PowerPoint 主要 Interop 組件中的所有類型都定義在 <xref:Microsoft.Office.Interop.PowerPoint> 命名空間中。 如需有關主要 interop 組件的詳細資訊，請參閱 < [Office 方案開發概觀&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)並[Office 主要 interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
##  <a name="WordOMDocumentation"></a> 使用 PowerPoint 物件模型文件  
 如需 PowerPoint 物件模型的完整資訊，您可以參閱 PowerPoint 主要 Interop 組件 (PIA) 參考和 VBA 物件模型參考。  
  
### <a name="primary-interop-assembly-reference"></a>主要 interop 組件參考  
 PowerPoint PIA 參考文件說明 PowerPoint 主要 Interop 組件中的類型。 這份文件可從下列位置：[PowerPoint 2010 主要 interop 組件參考](http://go.microsoft.com/fwlink/?LinkId=189588)。  
  
 如需有關設計的 PowerPoint PIA，例如類別和介面之間的差異以及 PIA 中的事件實作的方式，請參閱[的 Office 主要 interop 組件中類別和介面概觀](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>VBA 物件模型參考  
 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的 PowerPoint 物件模型。 如需詳細資訊，請參閱[PowerPoint 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 VBA 物件模型參考中的所有物件和成員都會對應至 PowerPoint 主要 Interop 組件 (PIA) 中的類型和成員。 例如，VBA 物件模型參考中的簡報物件對應至<xref:Microsoft.Office.Interop.PowerPoint.Presentation>PowerPoint PIA 中的型別。 雖然 VBA 物件模型參考提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 PowerPoint VSTO 增益集專案中使用這些程式碼範例，則必須將這個參考中的 VBA 程式碼轉譯為 Visual Basic 或 Visual C#。  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>自訂 PowerPoint 使用者介面  
 您可以使用下列方式來修改 PowerPoint 的 UI。  
  
|工作|如需詳細資訊|  
|----------|--------------------------|  
|建立自訂工作窗格。|[自訂工作窗格](../vsto/custom-task-panes.md)|  
|在功能區中新增自訂索引標籤。|[功能區概觀](../vsto/ribbon-overview.md)|  
|將自訂群組新增至功能區上的內建索引標籤。|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 如需自訂 PowerPoint 的 UI 和其他 Microsoft Office 應用程式的詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：您第一個 VSTO 增益集建立 powerpoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [開始進行程式設計 VSTO 增益集](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)   
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 主要 interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [中的 Office 程式開發的 PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199015)  
