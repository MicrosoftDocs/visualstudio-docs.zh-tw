---
title: Excel：開始程式設計檔層級自訂
description: 瞭解開始使用 Visual Studio 來建立 Microsoft Office Excel 檔層級自訂的須知。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: de5d7529e0bd8bc99eb4f375a31dab9ea9520234
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860720"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>開始程式設計 Excel 的檔層級自訂
  如果您剛開始使用 Visual Studio 來建立 Microsoft Office Excel 的檔層級自訂，以下是您需要知道的專案。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>瞭解 Excel 檔層級自訂的運作方式
 Excel 的檔層級自訂是以單一活頁簿為基礎。 若要開始使用自訂，終端使用者會開啟活頁簿，或從 Excel 範本建立活頁簿。 活頁簿中的事件（例如，在儲存格中輸入或按一下按鈕和功能表項目）可以呼叫元件中的事件處理方法。 當活頁簿關閉時，自訂所提供的功能將無法在 Excel 中使用，只可在包含這些功能的檔中使用。

 如需詳細資訊，請參閱 [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

## <a name="create-document-level-projects-for-excel"></a>建立 Excel 的檔層級專案
 若要建立 Excel 的檔層級自訂，請在 [ **新增專案** ] 對話方塊中使用 [Excel 活頁簿] 或 [excel 範本] 專案範本。 這些範本包含必要的組件參考和專案檔。

 如需如何建立 Excel 檔層級專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需專案範本的詳細資訊，請參閱 [Office 專案範本總覽](../vsto/office-project-templates-overview.md)。

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>使用主專案和主控制項程式設計 Excel 活頁簿
 *主專案* 和 *主控制項* 是可為使用 Visual Studio 所建立的檔層級自訂提供程式設計模型的類別。

 主專案提供程式碼的進入點，而且也可以作為主控制項和 Windows Forms 控制項的容器。 在 Excel 的檔層級專案中，這些主專案是由 `ThisWorkbook` 、 `Sheet1` 、 `Sheet2` 和類別表示 `Sheet3` 。

 主控制項是以原生 Excel 物件（例如清單物件和範圍）為基礎。 主控制項提供與原生 Excel 物件類似的功能，但它們也有新的事件、設計工具支援和資料系結功能。 它們在您的專案程式碼和 IntelliSense 中會顯示為第一類物件，讓您可以更輕鬆地直接在程式碼中參考特定物件，而不需要流覽 Excel 物件模型。

 如需詳細資訊，請參閱下列主題：

- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)

- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)

- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>自訂 Excel 的使用者介面
 大部分的 Microsoft Office 解決方案都會修改 Office 應用程式 (UI) 的使用者介面，以提供一些方法讓使用者與方案互動。 有許多方式可讓您使用檔層級自訂來修改 Excel 的 UI。 例如，您可以將控制項加入至功能區，也可以顯示執行窗格。 如需詳細資訊，請參閱 [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

 您也可以直接在 Visual Studio 中開啟與專案相關聯的活頁簿。 在 Visual Studio 中開啟活頁簿時，您可以使用 Excel 使用者介面來修改活頁簿。 您也可以使用活頁簿作為設計介面，讓您將控制項拖曳至工作表。 如需詳細資訊，請參閱 [Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。

## <a name="use-data-binding"></a>使用資料系結
 主控制項也會在您可以從 [ **資料來源** ] 視窗拖曳的控制項清單中。 以這種方式加入主控制項時，會自動將這些控制項系結至您使用視窗所設定的資料來源。 若未撰寫任何程式碼，您可以顯示資料庫、web 服務和商務物件的資料。 如需詳細資訊，請參閱 [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

## <a name="next-steps"></a>下一步
 若要瞭解如何建立 Excel 的檔層級自訂，請參閱 [逐步解說：建立 excel 的第一個檔層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)。 本逐步解說將為您介紹 Visual Studio 中的 Office 程式開發工具，以及適用于 Excel 檔層級自訂的程式設計模型。

 如需逐步解說 Excel 專案中一些常見工作的主題清單，請參閱 [Office 程式設計的一般](../vsto/common-tasks-in-office-programming.md)工作。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)
- [Excel 方案](../vsto/excel-solutions.md)
- [逐步解說：建立 Excel 的第一個檔層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
