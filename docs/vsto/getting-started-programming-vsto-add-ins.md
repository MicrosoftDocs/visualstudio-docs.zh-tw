---
title: VSTO 增益集進行程式設計快速入門
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7249c3971c8008f70b9e5add79adddde17fe6a82
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="get-started-programming-vsto-add-ins"></a>VSTO 增益集進行程式設計快速入門
  您可以使用 VSTO 增益集來自動化 Microsoft Office 應用程式、擴充應用程式的功能，以及自訂應用程式的使用者介面 (UI)。 如需 VSTO 增益集與其他類型 Office 方案的系統相比較您可以使用 Visual Studio 建立，請參閱[Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>建立 VSTO 增益集專案中  
 使用其中一個 VSTO 增益集專案中的範本建立 VSTO 增益集專案中**新專案** 對話方塊。 這些範本包含必要的組件參考和專案檔。 Visual Studio 為 Office 中的大部分應用程式，提供 VSTO 增益集專案範本。  
  
 如需如何建立 VSTO 增益集專案的詳細資訊，請參閱[How to： 在 Visual Studio 建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需專案範本的詳細資訊，請參閱[Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## <a name="develop-vsto-add-in-projects"></a>開發 VSTO 增益集專案  
 當您建立 VSTO 增益集專案時，Visual Studio 會自動建立*ThisAddIn.vb* (在[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) 或*ThisAddIn.cs* （C# 中） 程式碼檔案。 這個檔案包含`ThisAddIn`類別，提供 VSTO 增益集的基礎。 載入或卸載 VSTO 增益集時，您可以使用這個類別的成員來執行程式碼，以存取主應用程式的物件模型及擴充應用程式的功能。 如需詳細資訊，請參閱[程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。  
  
## <a name="automate-applications-by-using-the-object-models"></a>使用物件模型自動化應用程式  
 Microsoft Office 應用程式的物件模型公開許多您可以在 VSTO 增益集中進行程式設計的類型。 您可以使用這些類型將應用程式自動化。 例如，您可以在 Outlook 中以程式設計的方式建立和傳送電子郵件訊息，也可以在 Word 中開啟文件和加入內容。 如需如何存取主應用程式碼中的物件模型的詳細資訊，請參閱[程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。  
  
 如需特定的 Microsoft Office 應用程式之物件模型的詳細資訊，請參閱下列主題：  
  
-   [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)  
  
-   [Word 物件模型概觀](../vsto/word-object-model-overview.md)  
  
-   [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath 方案](../vsto/infopath-solutions.md)  
  
-   [PowerPoint 方案](../vsto/powerpoint-solutions.md)  
  
-   [專案的方案](../vsto/project-solutions.md)  
  
-   [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>自訂應用程式的使用者介面  
 使用 VSTO 增益集自訂主應用程式 UI 的方法有很多：  
  
-   對於 Excel 和 Word，您可以將 Managed 控制項加入文件。 如需詳細資訊，請參閱[擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
-   如果應用程式支援的話，您可以自訂功能區。 如需詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
-   如果應用程式支援的話，您可以建立自訂工作窗格。 如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
-   針對 Outlook，您可以建立自訂表單區域。 如需詳細資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
-   對於所有 Microsoft Office 應用程式，您可以在 VSTO 增益集中顯示 Windows Form。  
  
 如需如何自訂的 Microsoft Office 應用程式 UI 的詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="next-steps"></a>後續步驟  
 若要了解如何建立 VSTO 增益集，請參閱下面的逐步解說：  
  
-   [逐步解說： 建立 Excel 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [逐步解說： 建立第一個 VSTO 增益集的 Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [逐步解說： 建立 PowerPoint 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [逐步解說： 建立第一個 VSTO 增益集專案](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [逐步解說： 建立 Word 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 這些逐步解說會為您介紹 Visual Studio 中的 Office Developer Tools，以及 VSTO 增益集的程式撰寫模型。  
  
 如需引導您完成一些常見的工作，在 Office 專案中的主題，請參閱[Office 程式設計的一般工作](../vsto/common-tasks-in-office-programming.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [開始&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [撰寫 VSTO 增益集](../vsto/programming-vsto-add-ins.md)  
  
  