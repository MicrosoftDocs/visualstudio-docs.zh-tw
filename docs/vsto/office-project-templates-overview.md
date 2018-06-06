---
title: Office 專案範本概觀
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dfd3db7a029497a0f9a5b5c2c6c89cde38524c23
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692609"
---
# <a name="office-project-templates-overview"></a>Office 專案範本概觀
  Visual Studio 中的 Microsoft Office 開發人員工具包含專案範本，用來建立下列類型的 Office 方案：  
  
-   [文件層級自訂](#DocLevel)  
  
-   [VSTO 增益集](#AppLevel)  
  
 這些類型的 Office 方案的詳細比較，請參閱[Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 Office 專案範本位於 [ **新增專案** ] 對話方塊之 [ **Visual C#** ] 和 [ **Visual Basic** ] 語言節點的 [ **Office** ] 節點底下。 每個範本都會根據目標應用程式產生具有適當組態的專案，包括組件參考和偵錯設定。  
  
 每個專案都會提供檔案和程式碼，協助您建立特定類型的方案。 針對每個專案產生的程式碼都包含開機和關機事件處理常式。 您可以在這些事件處理常式中加入程式碼，以在載入方案時將方案初始化，並在卸載方案時將方案清除。 如需詳細資訊，請參閱[Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)和[Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
> [!NOTE]  
>  特定 Visual Studio 版本隨附 Office 開發工具。 如需詳細資訊，請參閱[設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。  
  
##  <a name="DocLevel"></a> 文件層級自訂  
 [ **新增專案** ] 對話方塊中的 [ **Office** ] 節點提供下列專案範本，讓您開始建立 Word 和 Excel 文件層級的自訂：  
  
-   **Word 2013 和 2016 VSTO 文件**  
  
-   **Word 2013 和 2016 VSTO 範本**  
  
-   **Excel 2013 和 2016 VSTO 活頁簿**  
  
-   **Excel 2013 和 2016 VSTO 範本**  
  
-   **Word 2010 VSTO 文件**  
  
-   **Word 2010 VSTO 範本**  
  
-   **Excel 2010 VSTO 活頁簿**  
  
-   **Excel 2010 VSTO 範本**  
  
 [Word 文件] 和 [Excel 活頁簿] 專案範本提供程式碼，讓您開始建立以特定文件或活頁簿為基礎的方案。 在這些類型的方案中，您的程式碼只有在 Word 或 Excel 中開啟相關聯的文件時才會執行。  
  
 [Word 範本] 和 [Excel 範本] 專案範本的運作方式與 [Word 文件] 和 [Excel 活頁簿] 專案範本完全相同。 不過，[Word 範本] 和 [Excel 範本] 專案範本可讓使用者以您方案中的自訂範本，輕鬆地建立新的本機文件或活頁簿複本。 使用者透過範本建立的新文件會具有您方案中的功能。  
  
> [!NOTE]  
>  參考 Managed 程式碼擴充的 Word 範本不能當做全域 VSTO 增益集。如果是從 Word 的 Startup 目錄載入該範本，則不會呼叫該組件。 如需詳細資訊，請參閱[全域範本和 Excel 增益集 （.xla 檔案） 的限制](#Limitations)  
  
 如需開始使用這些專案類型的詳細資訊，請參閱下列主題：  
  
-   [程式文件層級自訂](../vsto/programming-document-level-customizations.md)  
  
-   [Word 方案](../vsto/word-solutions.md)  
  
-   [Excel 方案](../vsto/excel-solutions.md)  
  
-   [逐步解說： 建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [逐步解說： 建立 Excel 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a> VSTO 增益集  
 [新增專案]  對話方塊中的 [Office/SharePoint]  節點提供下列專案範本，讓您開始建立 VSTO 增益集。  
  
-   **Excel 2013 和 2016 VSTO 增益集**  
  
-   **InfoPath 2013 VSTO 增益集**  
  
-   **Outlook 2013 和 2016 VSTO 增益集**  
  
-   **PowerPoint 2013 和 2016 增益集**  
  
-   **Project 2013 和 2016 增益集**  
  
-   **Visio 2013 和 2016 增益集**  
  
-   **Word 2013 和 2016 增益集**  
  
-   **Excel 2010 增益集**  
  
-   **InfoPath 2010 增益集**  
  
-   **Outlook 2010 增益集**  
  
-   **PowerPoint 2010 增益集**  
  
-   **Project 2010 增益集**  
  
-   **Visio 2010 增益集**  
  
-   **Word 2010 增益集**  
  
 當您建立以上述其中一種專案範本為基礎的專案時，會在開啟相關聯的應用程式時執行您方案中的程式碼。 與文件層級專案不同，您的程式碼並未與單一文件相關聯。  
  
 如需開始使用這些專案類型的詳細資訊，請參閱下列主題：  
  
-   [VSTO 增益集進行程式設計快速入門](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [撰寫 VSTO 增益集](../vsto/programming-vsto-add-ins.md)  
  
-   [逐步解說： 建立 Excel 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [逐步解說： 建立第一個 VSTO 增益集的 Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [逐步解說： 建立 PowerPoint 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [逐步解說： 建立第一個 VSTO 增益集專案](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [逐步解說： 建立 Word 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## <a name="document-vs-template-solutions"></a>文件和範本方案比較  
 設計 Word 文件或 Excel 活頁簿適用的方案時，必須決定向使用者提供這份文件的最佳方式。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 在某些情況下，您或許希望分發給每位使用者一件複本。 此時，請使用 Excel 或 Word 文件專案建立您的方案。  
  
 而在其他情況下，您或許要將範本放在伺服器上，讓每一位使用者都可以開啟這個範本，然後將本機複本另存為文件。 此時，請使用 Excel 或 Word 範本專案建立您的方案。  
  
## <a name="comparison"></a>比較  
 下表列出文件與範本之間的差異：  
  
|文件|範本|  
|---------------|---------------|  
|除非文件已設定成唯讀，否則使用者可以開啟並且修改文件。 任何儲存的變更都會保存在原始文件中。|使用者可以開啟範本做為新文件來建立本機複本。 除非授與他們特別的使用權限，否則他們不能修改原始文件。|  
|文件開啟時會引發 <xref:Microsoft.Office.Tools.Word.Document.Open> 事件。|範本開啟時會引發 <xref:Microsoft.Office.Tools.Word.Document.New> 事件。|  
  
##  <a name="Limitations"></a> 全域範本和 Excel 增益集 （.xla 檔案） 的限制  
 文件、活頁簿及範本可能無法像全域範本或 Excel VSTO 增益集 (.xla 檔案) 一般正常運作。  
  
## <a name="word-templates"></a>Word 範本  
 如果 Microsoft Office Word 範本具有 Managed 程式碼擴充，當範本是以全域範本的形式附加，或是從 Word 的 [啟動] 目錄載入時，便不會呼叫專案組件。 此外，文件也無法辨識屬於 Office 方案一部分的範本格式。  
  
## <a name="excel-add-ins-xla-files"></a>Excel 增益集 (.xla 檔)  
 目前沒有可建立 Excel VSTO 增益集 (.xla 檔案) 的 Office 專案。 雖然可以將活頁簿存成 .xla 檔案，但這不是支援的作業，不建議這樣做。 如果將具有 managed 程式碼擴充，為活頁簿**Microsoft Office Excel 增益集 (\*.xla)** 檔案中，您可以選取在**增益集**套用至另一個活頁簿的對話方塊。 在某些情況下，套用 VSTO 增益集以後，程式碼會在目標活頁簿中執行，但是目前並不支援這樣使用 Office 方案。  
  
## <a name="see-also"></a>另請參閱  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [開始使用適用於 Excel 的文件層級自訂程式設計](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [開始使用 Word 的文件層級自訂程式設計](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [VSTO 增益集進行程式設計快速入門](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  