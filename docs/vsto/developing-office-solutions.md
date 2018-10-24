---
title: 開發 Office 方案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a95c5f5767e227c35763cfaea1e3619093fffda3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833059"
---
# <a name="develop-office-solutions"></a>開發 Office 方案
  在您使用 Visual Studio 中的 Office Developer Tools 來設計專案並且設定專案檔之後，即可開始專注於實作程式碼和自訂使用者介面 (UI)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  想要開發解決方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集較小的使用量，相較於 VSTO 增益集和解決方案，而且您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3、 以及 XML 來建置。  
  
## <a name="office-solutions-programming-model"></a>Office 方案程式設計模型  
 Office 物件模型會公開您可以對其進行程式設計的各種物件。 每當您使用 Managed 程式碼進行 Office 方案程式設計時，您會撰寫使用 Office 主要 Interop 組件中類型的程式碼。 在您使用 Visual Studio 中的 Office 專案範本建立的方案中，也可以直接在專案中針對產生的類別撰寫程式碼。 如需詳細資訊，請參閱 <<c0> [ 撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)。  
  
## <a name="program-different-types-of-office-solutions"></a>程式的不同類型的 Office 方案  
 您建立的方案類型，會決定可以在專案中使用的功能。 例如，您可以在設計階段從 Visual Studio 中的 [工具箱] 拖曳項目，藉此將 Windows Form 控制項和擴充的 Office 控制項 (名為 **「主控制項」** (Host Control)) 加入文件層級自訂。 不過，如果您要開發 VSTO 增益集，就只能藉由撰寫程式碼的方式，在執行階段將這類控制項加入文件。  
  
 如需不同類型解決方案特有功能的詳細資訊，請參閱下列主題：  
  
- [程式設計 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。  
  
- [程式文件層級自訂](../vsto/programming-document-level-customizations.md)。  
  
- [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
  可協助您規劃 Office 方案和程序，以協助您建立專案的背景資訊，請參閱[設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)|描述在 Office 方案中撰寫程式碼的不同層面。|  
|[程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)|提供 VSTO 增益集和相關的程式設計工作的程式設計模型概觀。|  
|[程式文件層級自訂](../vsto/programming-document-level-customizations.md)|提供文件層級自訂和相關程式設計工作的程式設計模型概觀。|  
|[Office UI 自訂](../vsto/office-ui-customization.md)|描述可以使用 VSTO 增益集和文件層級自訂，以不同方式自訂 Office 應用程式 UI。|  
|[在 Office 方案中的資料](../vsto/data-in-office-solutions.md)|描述您可以不同方式使用 Office 方案中的資料，例如將資料繫結至控制項和快取文件層級自訂中的資料。|  
|[自動儲存如何影響 Office 方案](./how-autosave-impacts-office-solutions.md)|描述您可能需要將 Office 方案時啟用 自動儲存的調整。|
|[Office 方案進行疑難排解](../vsto/troubleshooting-office-solutions.md)|提供建立 Office 方案時可能遇到之常見問題的解決提示。|  
|[Office 中的執行緒支援](../vsto/threading-support-in-office.md)|提供在 Office 方案中使用多個執行緒的概觀。|  
|[Office 專案中的協助工具](../vsto/accessibility-in-office-projects.md)|描述在 Office 方案中可用的協助工具功能。|  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立和修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [如何： 讀取和寫入文件屬性](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [如何： 以 Office 多語系使用者介面為目標](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [您第一個 VSTO 增益集建立適用於 Excel 的逐步解說：](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [逐步解說： 建立您第一個適用於 Excel 的文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [逐步解說： 建立您第一個 VSTO 增益集適用於 Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [逐步解說： 建立 PowerPoint 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [逐步解說： 建立您第一個 VSTO 增益集專案](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [逐步解說： 建立 Word 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [逐步解說： 建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  