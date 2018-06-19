---
title: 開始使用 Word 的文件層級自訂程式設計
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5bed5c08e15861840a34960d186b408fb86085d
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448850"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>開始使用 Word 的文件層級自訂程式設計
  如果您剛開始使用 Visual Studio 建立 Microsoft Office word 的文件層級自訂，以下是您需要知道。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>了解如何文件層級自訂的 Word 工作  
 單一文件會根據您所建立的每個 Word 自訂。 若要開始使用自訂，終端使用者開啟文件，或從 Word 範本建立文件。 在文件，例如將游標移到特定區域，或按一下按鈕和功能表項目，事件可以呼叫組件中的事件處理方法。 文件關閉時，提供自訂功能就不再可用在 Word 中。  
  
 如需詳細資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## <a name="create-document-level-projects-for-word"></a>建立 Word 的文件層級專案  
 若要建立 Word 的文件層級自訂，請使用 [Word 文件或 Word 範本專案範本中的**新專案**] 對話方塊。 這些範本包含必要的組件參考和專案檔。  
  
 如需如何建立 Word 的文件層級專案的詳細資訊，請參閱[How to： 在 Visual Studio 建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需專案範本的詳細資訊，請參閱[Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>程式使用主項目主控制項的 Word 文件  
 *主項目*和*主控制項*一些類別，可用於文件層級自訂程式設計模型。  
  
 主項目提供您的程式碼的進入點，也可以做為容器的主控制項和 Windows Form 控制項。 在 word 文件層級專案中，主項目由`ThisDocument`類別。  
  
 主控制項根據原生 Word 物件，例如內容控制項、 書籤，以及 XML 節點。 主控制項提供類似的功能的原生 Word 物件，但也有新的事件、 設計工具支援和資料繫結功能。 它們會顯示為第一級物件和 IntelliSense，讓您更輕鬆地直接在您的程式碼中的特定物件而不需要瀏覽 Word 物件模型參考中的專案程式碼。  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [程式文件層級自訂](../vsto/programming-document-level-customizations.md)  
  
-   [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>自訂 Word 使用者介面  
 大部分的 Microsoft Office 方案的 Office 應用程式提供某些使用者互動與方案的方式修改使用者介面 (UI)。 有許多方法，您可以在其中修改 Word 的 UI 使用文件層級自訂。 例如，您可以將控制項加入 功能區中，並可以顯示執行窗格。 如需詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
 您也可以開啟您直接在 Visual Studio 中的專案相關聯的文件。 在 Visual Studio 中開啟文件時，您可以使用 Word 使用者介面來修改文件。 您也可以使用與設計介面，可讓您將控制項拖曳至其本身的文件。 如需詳細資訊，請參閱[Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## <a name="bind-controls-to-data"></a>將控制項繫結至資料  
 內容控制項和<xref:Microsoft.Office.Tools.Word.Bookmark>控制項的控制項，您可以將從清單中的**資料來源**視窗。 加入內容控制項和書籤在這個方法會自動繫結至資料來源設定使用視窗。 而不需要撰寫任何程式碼，您可以顯示來自資料庫、 服務和商務物件資料。 如需詳細資訊，請參閱[資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## <a name="next-steps"></a>後續步驟  
 若要了解如何建立 Word 的文件層級自訂，請參閱[逐步解說： 建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)。 本逐步解說為您介紹 Visual Studio 和 Word 文件層級自訂的程式設計模型中的 Office 開發工具。  
  
 如需引導您完成一些常見的工作，在 Word 專案中的主題，請參閱[Office 程式設計的一般工作](../vsto/common-tasks-in-office-programming.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [程式文件層級自訂](../vsto/programming-document-level-customizations.md)   
 [Word 方案](../vsto/word-solutions.md)   
 [逐步解說： 建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)  
  
  