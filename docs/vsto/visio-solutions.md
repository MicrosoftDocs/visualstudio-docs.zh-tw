---
title: "Visio 方案 |Microsoft 文件"
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
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 558ddc7a9c0fee5305052143edaca2b88b097723
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="visio-solutions"></a>Visio 方案
  Visual Studio 提供的專案範本可用來建立 Microsoft Office Visio 的 VSTO 增益集。 您可以使用 VSTO 增益集來自動化 Visio、擴充 Visio 功能，或自訂 Visio 的使用者介面 (UI)。  
  
 如需 VSTO 增益集的詳細資訊，請參閱下列主題： [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 和 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。如果您不熟悉使用 Microsoft Office 進行程式設計，請參閱[入門 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/getting-started-office-development-in-visual-studio.md)。  
  
 **適用對象：** 本主題資訊適用於 Visio 2010 的 VSTO 增益集專案。 如需詳細資訊，請參閱 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
## <a name="automating-visio-by-using-the-visio-object-model"></a>使用 Visio 物件模型自動化 Visio  
 Visio 物件模型公開許多可用於自動化 Visio 的類別，來建立組織圖、流程圖、專案時間軸、網路圖表、辦公室等多種圖表。 應用程式開發介面可讓您撰寫程式碼以完成一般工作：  
  
-   在圖表中建構並放置圖形和文字。  
  
-   根據商務邏輯和使用者輸入管理圖形行為。  
  
-   控制圖表的視覺效果，例如移動瀏覽和縮放。  
  
-   自訂應用程式 UI。  
  
-   將外部資料匯入 Visio、連結至圖形，並以圖形方式顯示於頁面上。  
  
 [Working with Visio Documents](../vsto/working-with-visio-documents.md) 和 [Working with Visio Shapes](../vsto/working-with-visio-shapes.md)向您示範使用 Visio 物件模型處理文件和圖形的逐步程序和程式碼範例。  
  
 若要存取 VSTO 增益集中的 Visio 物件模型，請使用專案中 `Application` 類別的 `ThisAddIn` 欄位。 `Application`欄位傳回 Microsoft.Office.Interop.Visio.Application 物件，代表 Visio 目前執行個體。 如需詳細資訊，請參閱 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 呼叫 Visio 物件模型時，您使用的類型是由 Visio 的主要 Interop 組件 (PIA) 所提供。 PIA 的作用，如同 VSTO 增益集中 Managed 程式碼與 Visio 中 COM 物件模型之間的橋樑。 Visio PIA 中的所有類型都定義 Microsoft.Office.Interop.Visio 命名空間中。 如需主要 interop 組件的詳細資訊，請參閱[Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)和[Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
## <a name="visio-object-model-overview"></a>Visio 物件模型概觀  
 您可以在 [Visio Object Model Overview](../vsto/visio-object-model-overview.md)中找到 Visio 物件模型的概觀，其包含 Visio 物件模型參考和 SDK 的連結。  
  
## <a name="customizing-the-user-interface-of-visio"></a>自訂 Visio 的使用者介面  
 Visio UI 有下列自訂選項。  
  
|工作|如需詳細資訊|  
|----------|--------------------------|  
|自訂功能區。|[功能區概觀](../vsto/ribbon-overview.md)|  
  
 如需 Visio 自訂 UI 的相關資訊，請參閱 VBA 參考文件的 [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) 類別。  
  
## <a name="see-also"></a>請參閱  
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [Visio 2010 中的 Office 程式開發](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  