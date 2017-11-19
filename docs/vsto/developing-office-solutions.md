---
title: "開發 Office 方案 |Microsoft 文件"
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
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 478bd6d27d6e4ef0fe75891d95cdc4b3258a74e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="developing-office-solutions"></a>開發 Office 方案
  在您使用 Visual Studio 中的 Office Developer Tools 來設計專案並且設定專案檔之後，即可開始專注於實作程式碼和自訂使用者介面 (UI)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
## <a name="office-solutions-programming-model"></a>Office 方案程式設計模型  
 Office 物件模型會公開您可以對其進行程式設計的各種物件。 每當您使用 Managed 程式碼進行 Office 方案程式設計時，您會撰寫使用 Office 主要 Interop 組件中類型的程式碼。 在您使用 Visual Studio 中的 Office 專案範本建立的方案中，也可以直接在專案中針對產生的類別撰寫程式碼。 如需詳細資訊，請參閱 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)。  
  
## <a name="programming-different-types-of-office-solutions"></a>不同類型 Office 方案的程式設計  
 您建立的方案類型，會決定可以在專案中使用的功能。 例如，您可以在設計階段從 Visual Studio 中的 [工具箱] 拖曳項目，藉此將 Windows Form 控制項和擴充的 Office 控制項 (名為 **「主控制項」** (Host Control)) 加入文件層級自訂。 不過，如果您要開發 VSTO 增益集，就只能藉由撰寫程式碼的方式，在執行階段將這類控制項加入文件。  
  
 如需不同類型解決方案特有功能的詳細資訊，請參閱下列主題：  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
-   [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
 若要可協助您規劃 Office 方案和程序，以協助您建立專案的背景資訊，請參閱 [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)|描述在 Office 方案中撰寫程式碼的不同層面。|  
|[Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)|提供 VSTO 增益集和相關的程式設計工作的程式設計模型概觀。|  
|[Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)|提供文件層級自訂和相關程式設計工作的程式設計模型概觀。|  
|[Office UI 自訂](../vsto/office-ui-customization.md)|描述可以使用 VSTO 增益集和文件層級自訂，以不同方式自訂 Office 應用程式 UI。|  
|[Office 方案的資料](../vsto/data-in-office-solutions.md)|描述您可以不同方式使用 Office 方案中的資料，例如將資料繫結至控制項和快取文件層級自訂中的資料。|  
|[自動儲存有何影響 Office 方案](./how-autosave-impacts-office-solutions.md)|描述您可能需要將 Office 方案時已啟用 調整。|
|[針對 Office 方案進行疑難排解](../vsto/troubleshooting-office-solutions.md)|提供建立 Office 方案時可能遇到之常見問題的解決提示。|  
|[Office 中的執行緒支援](../vsto/threading-support-in-office.md)|提供在 Office 方案中使用多個執行緒的概觀。|  
|[Office 專案中的協助工具](../vsto/accessibility-in-office-projects.md)|描述在 Office 方案中可用的協助工具功能。|  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立和修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [如何： 讀取和寫入文件屬性](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [如何： 為目標的 Office 多語系使用者介面](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [逐步解說：建立 Excel 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [逐步解說： 建立 Excel 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [逐步解說： 建立 Outlook 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [逐步解說： 建立 PowerPoint 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [逐步解說： 建立專案的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [逐步解說： 建立 Word 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [逐步解說：建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  