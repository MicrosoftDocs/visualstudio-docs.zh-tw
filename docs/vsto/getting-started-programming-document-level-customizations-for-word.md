---
title: 開始程式設計 Word 的檔層級自訂
description: 瞭解如何使用 Visual Studio 開始為 Microsoft Office Word 建立檔層級自訂的須知。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: e9420ab02b5f402dd39e5ca1713b911a10932dfb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845176"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>開始程式設計 Word 的檔層級自訂
  如果您剛開始使用 Visual Studio 來建立 Microsoft Office Word 的檔層級自訂，以下是您需要知道的專案。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>瞭解 Word 工作的檔層級自訂
 您所建立的每個單字自訂都是以單一檔為基礎。 若要開始使用自訂，終端使用者會開啟檔或從 Word 範本建立檔。 檔中的事件（例如，將游標移到特定區域，或是按一下按鈕和功能表項目）可以呼叫元件中的事件處理方法。 當檔關閉時，自訂所提供的功能就無法再于 Word 中使用。

 如需詳細資訊，請參閱 [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

## <a name="create-document-level-projects-for-word"></a>建立 Word 的檔層級專案
 若要建立 Word 的檔層級自訂，請使用 [ **新增專案** ] 對話方塊中的 word 檔或 word 範本專案範本。 這些範本包含必要的組件參考和專案檔。

 如需如何建立 Word 檔層級專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。 如需專案範本的詳細資訊，請參閱 [Office 專案範本總覽](../vsto/office-project-templates-overview.md)。

## <a name="program-word-documents-by-using-host-items-host-controls"></a>使用主專案主控制項編寫 Word 檔
 *主專案* 和 *主控制項* 是提供檔層級自訂程式設計模型的類別。

 主專案提供程式碼的進入點，而且也可以作為主控制項和 Windows Forms 控制項的容器。 在 Word 的檔層級專案中，主專案是由類別表示 `ThisDocument` 。

 主控制項是以原生字組物件為基礎，例如內容控制項、書簽和 XML 節點。 主控制項提供與原生 Word 物件類似的功能，但它們也有新的事件、設計工具支援和資料系結功能。 它們在您的專案程式碼和 IntelliSense 中會顯示為第一類物件，讓您可以更輕鬆地直接在程式碼中參考特定物件，而不需要流覽 Word 物件模型。

 如需詳細資訊，請參閱下列主題：

- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)

- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)

- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>自訂 Word 的使用者介面
 大部分的 Microsoft Office 解決方案都會修改 Office 應用程式 (UI) 的使用者介面，以提供一些方法讓使用者與方案互動。 有許多方式可讓您使用檔層級自訂來修改 Word 的 UI。 例如，您可以將控制項加入至功能區，而且可以顯示執行窗格。 如需詳細資訊，請參閱 [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

 您也可以直接在 Visual Studio 中開啟與專案相關聯的檔。 當檔在 Visual Studio 中開啟時，您可以使用 Word 使用者介面來修改檔。 您也可以使用檔做為設計介面，讓您將控制項拖曳到控制項上。 如需詳細資訊，請參閱 [Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。

## <a name="bind-controls-to-data"></a>將控制項系結至資料
 內容控制項和控制項位於 <xref:Microsoft.Office.Tools.Word.Bookmark> 您可以從 [ **資料來源** ] 視窗拖曳的控制項清單中。 以這種方式加入內容控制項和書簽，會自動將其系結至您使用視窗所設定的資料來源。 若未撰寫任何程式碼，您可以顯示資料庫、服務和商務物件的資料。 如需詳細資訊，請參閱 [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

## <a name="next-steps"></a>後續步驟
 若要瞭解如何建立 Word 的檔層級自訂，請參閱 [逐步解說：建立 word 的第一個檔層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)。 本逐步解說將為您介紹 Visual Studio 中的 Office 程式開發工具，以及 Word 檔層級自訂的程式設計模型。

 如需逐步解說 Word 專案中一些常見工作的主題清單，請參閱 [Office 程式設計的一般](../vsto/common-tasks-in-office-programming.md)工作。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)
- [Word 方案](../vsto/word-solutions.md)
- [逐步解說：建立 Word 的第一個檔層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [Word 物件模型總覽](../vsto/word-object-model-overview.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
