---
title: "PowerPoint 方案 |Microsoft 文件"
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
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9dfa41bdecc7e47a0bf367409aac79d354daaad3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="powerpoint-solutions"></a>PowerPoint 方案
  Visual Studio 提供您可用來建立 Microsoft Office PowerPoint VSTO 增益集的專案範本。 您可以使用 VSTO 增益集來自動化 PowerPoint、擴充 PowerPoint 功能，或自訂 PowerPoint 使用者介面 (UI)。  
  
 如需 VSTO 增益集的詳細資訊，請參閱下列主題： [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 和 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。如果您不熟悉使用 Microsoft Office 進行程式設計，請參閱[入門 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/getting-started-office-development-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何： 建立增益集 Microsoft powerpoint？](http://go.microsoft.com/fwlink/?LinkId=132767)。  
  
## <a name="automating-powerpoint-by-using-the-powerpoint-object-model"></a>使用 PowerPoint 物件模型自動化 PowerPoint  
 PowerPoint 物件模型會公開您可用來自動化 PowerPoint 的許多類型。 這些類型可讓您撰寫程式碼來完成一般工作：  
  
-   以程式設計方式建立和格式化簡報。  
  
-   新增或移除簡報中的投影片。  
  
-   新增或變更投影片上的圖案。  
  
 若要從 VSTO 增益集存取 PowerPoint 物件模型，請使用您專案中 `Application` 類別的 `ThisAddIn` 欄位。 `Application` 欄位傳回的 <xref:Microsoft.Office.Interop.PowerPoint.Application> 物件代表目前的 PowerPoint 執行個體。 如需詳細資訊，請參閱 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 呼叫 PowerPoint 物件模型時，您使用的類型是由 PowerPoint 的主要 Interop 組件所提供。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與 PowerPoint 中 COM 物件模型之間的橋樑。 PowerPoint 主要 Interop 組件中的所有類型都定義在 <xref:Microsoft.Office.Interop.PowerPoint> 命名空間中。 如需主要 interop 組件的詳細資訊，請參閱[Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)和[Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
##  <a name="WordOMDocumentation"></a> 使用 PowerPoint 物件模型文件  
 如需 PowerPoint 物件模型的完整資訊，您可以參閱 PowerPoint 主要 Interop 組件 (PIA) 參考和 VBA 物件模型參考。  
  
### <a name="primary-interop-assembly-reference"></a>主要 Interop 組件參考  
 PowerPoint PIA 參考文件說明 PowerPoint 主要 Interop 組件中的類型。 您可以從下列位置取得這份文件： [PowerPoint 2010 主要 Interop 組件參考](http://go.microsoft.com/fwlink/?LinkId=189588)。  
  
 如需 PowerPoint PIA 設計的詳細資訊，例如 PIA 中類別和介面的差異以及 PIA 中實作事件的方式，請參閱 [Office 主要 Interop 組件中的類別和介面概觀](http://go.microsoft.com/fwlink/?LinkId=199885)。  
  
### <a name="vba-object-model-reference"></a>VBA 物件模型參考  
 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的 PowerPoint 物件模型。 如需詳細資訊，請參閱 [PowerPoint 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199770)。  
  
 VBA 物件模型參考中的所有物件和成員都會對應至 PowerPoint 主要 Interop 組件 (PIA) 中的類型和成員。 例如，VBA 物件模型參考中的簡報物件會對應至<xref:Microsoft.Office.Interop.PowerPoint.Presentation>PowerPoint PIA 中的型別。 雖然 VBA 物件模型參考提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 PowerPoint VSTO 增益集專案中使用這些程式碼範例，則必須將這個參考中的 VBA 程式碼轉譯為 Visual Basic 或 Visual C#。  
  
## <a name="customizing-the-user-interface-of-powerpoint"></a>自訂 PowerPoint 的使用者介面  
 您可以使用下列方式來修改 PowerPoint 的 UI。  
  
|工作|如需詳細資訊|  
|----------|--------------------------|  
|建立自訂工作窗格。|[自訂工作窗格](../vsto/custom-task-panes.md)|  
|在功能區中新增自訂索引標籤。|[功能區概觀](../vsto/ribbon-overview.md)|  
|將自訂群組新增至功能區上的內建索引標籤。|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 如需自訂 PowerPoint 的 UI 及其他 Microsoft Office 應用程式的詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說： 建立 PowerPoint 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 中的 Office 程式開發](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  