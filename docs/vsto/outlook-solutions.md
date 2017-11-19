---
title: "Outlook 方案 |Microsoft 文件"
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
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e0784662a1c48602dd8f93f5ae97c0a69192c3a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="outlook-solutions"></a>Outlook 方案
  Visual Studio 提供的專案範本可用來建立 Microsoft Office Outlook 的 VSTO 增益集。 您可以使用 VSTO 增益集來自動化 Outlook、擴充 Outlook 功能，或自訂 Outlook 的使用者介面 (UI)。 如需 VSTO 增益集的詳細資訊，請參閱 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
## <a name="creating-an-outlook-vsto-add-in-project"></a>建立 Outlook VSTO 增益集專案  
 使用 [新增專案]  對話方塊中的 [Outlook 增益集]  專案範本建立 Outlook 專案。 這個範本包含必要的組件參考和專案檔。  
  
 如需如何建立 VSTO 增益集專案的詳細資訊，請參閱[How to： 建立 Visual Studio 中的 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需專案範本的詳細資訊，請參閱[Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO 增益集程式設計模型  
 當您建立 Outlook VSTO 增益集專案時，Visual Studio 會產生名為 `ThisAddIn`的類別，這是解決方案的基礎。 這個類別會提供撰寫程式碼的起點，還會向 VSTO 增益集公開 Outlook 物件模型。  
  
 如需有關`ThisAddIn`類別和其他功能，您可以使用 VSTO 增益集中，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
## <a name="automating-outlook-by-using-the-outlook-object-model"></a>使用 Outlook 物件模型自動化 Outlook  
 Outlook 物件模型會公開您可用來自動化 Outlook 的許多類型。 這些類型可讓您撰寫程式碼以完成一般工作：  
  
-   以程式設計方式建立並傳送電子郵件訊息。  
  
-   傳送新的會議邀請。  
  
-   在 Outlook 資料夾中搜尋項目。  
  
 如需詳細資訊，請參閱 [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)。  
  
## <a name="customizing-the-user-interface-of-an-outlook-application"></a>自訂 Outlook 應用程式的使用者介面  
  
|工作|如需詳細資訊|  
|----------|--------------------------|  
|在 Outlook 偵測器的功能區中加入自訂索引標籤。|[功能區概觀](../vsto/ribbon-overview.md)|  
|將自訂群組加入 Outlook 偵測器的內建索引標籤。|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|  
|加入在 Outlook 偵測器中顯示的自訂工作窗格|[自訂工作窗格](../vsto/custom-task-panes.md)。|  
|加入擴充或取代現有 Outlook 表單的表單區域。|[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)|  
  
 如需自訂 Outlook 的 UI 及其他 Microsoft Office 應用程式的詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)|提供 Outlook 物件模型提供的物件概觀。|  
|[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)|說明 Visual Studio 提供的工具，它們可讓您更輕鬆地設計、開發及偵錯表單區域。|  
|[逐步解說：為您的 Outlook 建立第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|示範如何建立 Microsoft Office Outlook 的 VSTO 增益集。|  
|[Office 程式開發中的 Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199013)|您可以在 MSDN Library 中，找到有關開發 Outlook 方案 (不限於使用 Visual Studio 的 Office 程式開發) 之文章和參考文件的區域。|  
  
  