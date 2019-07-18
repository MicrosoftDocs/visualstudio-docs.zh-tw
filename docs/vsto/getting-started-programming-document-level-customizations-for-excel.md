---
title: Excel:開始使用文件層級自訂程式設計
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c1ff264eb1a4ca7afdc424cef7edf15bae06554
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402164"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>開始使用適用於 Excel 的文件層級自訂程式設計
  如果您剛開始使用 Visual Studio 建立適用於 Microsoft Office Excel 的文件層級自訂，以下是您需要知道。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>了解如何為文件層級自訂的 Excel 工作
 適用於 Excel 的文件層級自訂是以單一活頁簿為基礎。 若要開始使用自訂，使用者開啟活頁簿，或從 Excel 範本建立的活頁簿。 事件在活頁簿中，例如在儲存格中輸入或按一下按鈕和功能表項目，可以呼叫組件中的事件處理方法。 關閉活頁簿時，自訂所提供的功能已在 Excel 中，僅適用於文件包含它們。

 如需詳細資訊，請參閱 <<c0> [ 文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

## <a name="create-document-level-projects-for-excel"></a>建立適用於 Excel 的文件層級專案
 若要建立 Excel 的文件層級自訂，請使用 [在 Excel 活頁簿或 Excel 範本專案範本**新的專案**] 對話方塊。 這些範本包含必要的組件參考和專案檔。

 如需如何建立適用於 Excel 的文件層級專案的詳細資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需詳細的專案範本的詳細資訊，請參閱[Office 專案範本概觀](../vsto/office-project-templates-overview.md)。

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>程式所使用的 Excel 活頁簿主項目和主控制項
 *主項目*並*主控制項*是提供使用 Visual Studio 所建立的文件層級自訂程式設計模型的類別。

 主項目提供您的程式碼的進入點，它們也可以做為主控制項和 Windows Form 控制項的容器。 在適用於 Excel 的文件層級專案，這些主機項目都由`ThisWorkbook`， `Sheet1`， `Sheet2`，和`Sheet3`類別。

 主控制項是以原生的 Excel 物件，例如物件清單和範圍為基礎。 主控制項提供類似的功能，原生 Excel 物件，但它們也有新的事件、 設計工具支援，以及資料繫結功能。 它們會顯示為第一級的物件，在您的專案程式碼和 IntelliSense，可讓您更輕鬆地直接在您的程式碼中的特定物件參考，而不必瀏覽 Excel 物件模型中。

 如需詳細資訊，請參閱下列主題：

- [程式文件層級自訂](../vsto/programming-document-level-customizations.md)

- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)

- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>自訂 Excel 的使用者介面
 大部分的 Microsoft Office 解決方案會修改使用者介面 (UI)，提供一些方式，讓使用者與該解決方案互動的 Office 應用程式。 有許多方法，您可以在其中修改 Excel 的 UI 使用文件層級自訂。 比方說，您可以將控制項新增至功能區中，或您可以顯示執行窗格。 如需詳細資訊，請參閱 < [Office UI 自訂](../vsto/office-ui-customization.md)。

 您也可以開啟與您直接在 Visual Studio 中的專案相關聯的活頁簿。 在 Visual Studio 中開啟活頁簿時，您可以使用 Excel 使用者介面來修改活頁簿。 您也可以使用設計介面，可讓您將控制項拖曳到工作表活頁簿。 如需詳細資訊，請參閱 < [Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。

## <a name="use-data-binding"></a>使用資料繫結
 主控制項也會在清單中的控制項，您可以從拖曳**Zdroje dat**視窗。 將主控制項加入在這個方法會自動將它們繫結至資料來源所使用的視窗。 不需要撰寫任何程式碼，您可以顯示來自資料庫、 web 服務和商務物件資料。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

## <a name="next-steps"></a>後續步驟
 若要了解如何建立 Excel 文件層級自訂，請參閱[逐步解說：建立您第一個適用於 Excel 的文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)。 本逐步解說會向您介紹 Visual Studio 和 Excel 文件層級自訂的程式設計模型中的 Office 開發工具。

 如需逐步引導您完成一些常見工作，在 Excel 專案中的主題，請參閱[在 Office 程式設計中的一般工作](../vsto/common-tasks-in-office-programming.md)。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式文件層級自訂](../vsto/programming-document-level-customizations.md)
- [Excel 方案](../vsto/excel-solutions.md)
- [逐步解說：建立您第一個適用於 Excel 的文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
