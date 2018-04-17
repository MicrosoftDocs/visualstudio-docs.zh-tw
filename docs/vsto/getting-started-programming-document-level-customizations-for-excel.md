---
title: 適用於 Excel 的文件層級自訂程式設計入門 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f10e0c2d3dc7a561b4fff7ad74081e9a26570b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Excel 文件層級自訂的程式設計入門
  如果您剛開始使用 Visual Studio 建立 Microsoft Office excel 的文件層級自訂，以下是您需要知道。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>了解如何文件層級自訂的 Excel 工作  
 適用於 Excel 的文件層級自訂根據活頁簿。 若要開始使用自訂，終端使用者開啟活頁簿或 Excel 範本中建立的活頁簿。 比方說，在儲存格中輸入或按一下按鈕和功能表項目，活頁簿中的事件可以在組件中呼叫事件處理方法。 活頁簿關閉時，提供自訂功能便無法再在 Excel 中，僅適用於文件包含它們。  
  
 如需詳細資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## <a name="creating-document-level-projects-for-excel"></a>建立適用於 Excel 的文件層級專案  
 若要建立 Excel 的文件層級自訂，請使用 [在 Excel 活頁簿或 Excel 範本專案範本**新專案**] 對話方塊。 這些範本包含必要的組件參考和專案檔。  
  
 如需如何建立 Excel 文件層級專案的詳細資訊，請參閱[How to： 建立 Visual Studio 中的 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需專案範本的詳細資訊，請參閱[Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>使用 主項目和主控制項的程式設計 Excel 活頁簿  
 *主項目*和*主控制項*是提供使用 Visual Studio 建立的文件層級自訂的程式設計模型的類別。  
  
 主項目提供您的程式碼的進入點，也可以做為容器的主控制項和 Windows Form 控制項。 在 Excel 的文件層級專案中，這些主機項目都由`ThisWorkbook`， `Sheet1`， `Sheet2`，和`Sheet3`類別。  
  
 主控制項根據原生 Excel 物件，例如清單物件和範圍。 主控制項提供類似的功能的原生 Excel 物件，但也有新的事件、 設計工具支援和資料繫結功能。 它們會顯示為第一級物件和 IntelliSense，可讓您更輕鬆地直接在您的程式碼中的特定物件而不需要瀏覽 Excel 物件模型參考中的專案程式碼。  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>自訂 Excel 的使用者介面  
 大部分的 Microsoft Office 方案的 Office 應用程式提供某些使用者互動與方案的方式修改使用者介面 (UI)。 有許多方法，您可以在其中修改 Excel 的 UI 使用文件層級自訂。 例如，您可以將控制項加入 功能區中，或您可以顯示執行窗格。 如需詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
 您也可以開啟您直接在 Visual Studio 中的專案相關聯的活頁簿。 在 Visual Studio 中開啟活頁簿時，您可以使用 Excel 使用者介面來修改活頁簿。 您也可以使用活頁簿做為設計介面，可讓您將控制項拖曳到工作表。 如需詳細資訊，請參閱[Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## <a name="using-data-binding"></a>使用資料繫結  
 主控制項的控制項，您可以將從清單中也是**資料來源**視窗。 將主控制項加入在這個方法會自動繫結至資料來源設定使用視窗。 而不需要撰寫任何程式碼，您可以顯示來自資料庫、 web 服務和商務物件資料。 如需詳細資訊，請參閱[資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## <a name="next-steps"></a>後續步驟  
 若要了解如何建立 Excel 文件層級自訂，請參閱[逐步解說： 建立您的第一個文件層級自訂 Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)。 本逐步解說為您介紹 Visual Studio 和 Excel 文件層級自訂的程式設計模型中的 Office 開發工具。  
  
 如需引導您完成一些 Excel 專案中的一般工作的主題，請參閱[Office 程式設計的一般工作](../vsto/common-tasks-in-office-programming.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)   
 [Excel 方案](../vsto/excel-solutions.md)   
 [逐步解說： 建立 Excel 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)   
 [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  