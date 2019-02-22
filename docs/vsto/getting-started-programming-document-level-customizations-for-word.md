---
title: 開始使用 word 的文件層級自訂程式設計
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b8ac2efc6627eae017c7154743091b7682dc8ac
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869196"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>開始使用 word 的文件層級自訂程式設計
  如果您剛開始使用 Visual Studio 建立 Microsoft Office word 的文件層級自訂，以下是您需要知道。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>了解如何為文件層級自訂的 Word 工作  
 您所建立的每個 Word 自訂是以單一文件為基礎。 若要開始使用自訂，使用者開啟文件，或從 Word 範本建立文件。 事件在文件，例如將游標移到特定區域，或按一下按鈕和功能表項目，可以呼叫組件中的事件處理方法。 關閉文件時，已不再可用在 Word 中自訂所提供的功能。  
  
 如需詳細資訊，請參閱 <<c0> [ 文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## <a name="create-document-level-projects-for-word"></a>建立 Word 文件層級專案  
 若要建立 Word 的文件層級自訂，請使用 [中的 Word 文件或 Word 範本專案範本**新的專案**] 對話方塊。 這些範本包含必要的組件參考和專案檔。  
  
 如需如何建立 Word 文件層級專案的詳細資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需詳細的專案範本的詳細資訊，請參閱[Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>計劃使用主項目主控制項的 Word 文件  
 *主項目*並*主控制項*是提供文件層級自訂程式設計模型的類別。  
  
 主項目提供您的程式碼的進入點，它們也可以做為主控制項和 Windows Form 控制項的容器。 在 word 文件層級專案中，主項目由`ThisDocument`類別。  
  
 主控制項是以原生 Word 物件，例如內容控制項、 書籤，以及 XML 節點為基礎。 主控制項提供類似的功能，原生 Word 物件，但它們也有新的事件、 設計工具支援，以及資料繫結功能。 它們會顯示為第一級 IntelliSense，更輕鬆地直接在您的程式碼中的特定物件而不需要巡覽 Word 物件模型參考和專案程式碼中的物件。  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [程式文件層級自訂](../vsto/programming-document-level-customizations.md)  
  
-   [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>自訂 Word 的使用者介面  
 大部分的 Microsoft Office 解決方案會修改使用者介面 (UI)，提供一些方式，讓使用者與該解決方案互動的 Office 應用程式。 有許多方法，您可以在此修改所使用的文件層級自訂的 Word 的 UI。 例如，您可以將控制項新增至功能區中，而且可以顯示動作 窗格中。 如需詳細資訊，請參閱 < [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
 您也可以開啟與您直接在 Visual Studio 中的專案相關聯的文件。 在 Visual Studio 中開啟文件時，您可以使用 Word 使用者介面來修改文件。 您也可以使用設計介面，可讓您將控制項拖曳到文件。 如需詳細資訊，請參閱 < [Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## <a name="bind-controls-to-data"></a>將控制項繫結至資料  
 內容控制項和<xref:Microsoft.Office.Tools.Word.Bookmark>控制項的控制項，您可以將從清單中的**Zdroje dat**視窗。 加入內容控制項和設定為書籤在這個方法會自動將它們繫結至資料來源，您使用視窗設定。 不需要撰寫任何程式碼，您可以顯示來自資料庫、 服務和商務物件資料。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## <a name="next-steps"></a>後續步驟  
 若要了解如何建立 Word 的文件層級自訂，請參閱[逐步解說：建立第一個文件層級自訂 word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)。 本逐步解說會向您介紹 Visual Studio 和 Word 文件層級自訂的程式設計模型中的 Office 開發工具。  
  
 如需逐步引導您完成一些常見工作，在 Word 專案中的主題，請參閱[在 Office 程式設計中的一般工作](../vsto/common-tasks-in-office-programming.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [程式文件層級自訂](../vsto/programming-document-level-customizations.md)   
 [Word 方案](../vsto/word-solutions.md)   
 [逐步解說：建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)  
