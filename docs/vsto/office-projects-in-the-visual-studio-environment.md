---
title: Visual Studio 環境中的 Office 專案
description: 瞭解 Microsoft Office 專案的開發經驗如何與 Visual Studio 中的其他專案類型（例如 Windows Forms 專案）類似。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e183d5aca3fa856f45f322c2b79a76524b28005
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525156"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Visual Studio 環境中的 Office 專案
  開發 Microsoft Office 專案的方式與在 Visual Studio 中開發其他類型的專案 (例如 Windows Forms 專案) 類似。 在您建立或開啟 Office 專案時，專案項目會顯示在 [ **方案總管**] 中。 就文件層級專案而言，文件 (亦即 Word 文件或 Excel 活頁簿) 會在 Visual Studio 中開啟，並以如同視覺化設計工具的方式運作。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>方案總管中的專案專案
 在文件層級專案中，[ **方案總管** ] 會顯示下列預設項目：

- 專案所自訂之文件、活頁簿和工作表的節點。 這些節點是與文件、活頁簿和工作表相關聯之程式碼檔的容器。

- 與專案所自訂之文件、活頁簿和工作表相關聯的程式碼檔。 在 Word 專案中，程式碼檔是與 Word 文件或範本相關聯。 在 Excel 專案中，程式碼檔是與 Excel 活頁簿或範本相關聯，並且與活頁簿或範本中的每張工作表和圖表相關聯。

- 您不應該直接編輯的隱藏專案檔。 如需詳細資訊，請參閱 [隱藏的專案](#hiddenfiles)檔。

  在 VSTO 增益集專案中，方案總管  會顯示下列預設項目：

- 應用程式節點。 這個節點的名稱與主應用程式相同 (例如 **Word**、 **Excel** 或 **Outlook**)。 應用程式節點包含 ThisAddIn 程式碼檔。 也會提供 [ **主項目命名空間** ] 屬性。 如需此屬性的詳細資訊，請參閱 [Office 專案中的屬性](../vsto/properties-in-office-projects.md)。

- ThisAddIn 程式碼檔。 這個檔案包含針對您的 VSTO 增益集產生的 `ThisAddIn` 類別。 如需此類別的詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

- 您不應該直接編輯的隱藏專案檔。 如需詳細資訊，請參閱 [隱藏的專案](#hiddenfiles)檔。

### <a name="temporary-certificates"></a>暫時憑證
 Office 專案也包含名稱為 *專案名稱* _TemporaryKey.pfx 的暫時憑證。 這個憑證是用來簽署開發期間之專案的應用程式和部署資訊清單。 如需詳細資訊，請參閱 [授與信任給 office 方案](../vsto/granting-trust-to-office-solutions.md) 和 [安全的 office 方案](../vsto/securing-office-solutions.md)。

### <a name="hidden-project-files"></a><a name="hiddenfiles"></a> 隱藏的專案檔案
 預設會隱藏數個專案檔。 這些檔案是由 Visual Studio 所產生，並且會因專案類型而異。 若要顯示隱藏檔，請按一下 [方案總管]  中的 [顯示所有檔案] 。

 請勿修改隱藏專案檔。 不支援直接變更這些檔案，因為這麼做可能會損毀您的專案。 只要在文件中發生某些變更，就會重新產生隱藏專案檔。 如果您手動變更隱藏專案檔，則這些變更會在檔案重新產生時遺失。

## <a name="document-designer-in-document-level-projects"></a>檔層級專案中的檔設計工具
 Excel 和 Word 的文件層級專案提供一套設計工具，可將與您的專案相關聯的文件裝載於 Visual Studio 中。 這個設計工具可讓您直接修改文件，而不需要離開 Visual Studio 環境。

 若要以設計工具開啟文件，請按兩下 [ **方案總管** ] 中與文件相關聯的程式碼檔。 例如，若要以設計工具開啟 Excel 專案中的工作表 **Sheet1** ，請按兩下 **Sheet1** 程式碼檔。

 當您以設計工具修改文件時，可以利用 Office 應用程式的原生功能。 例如，您可以在文件或工作表中輸入文字，也可以使用功能區來執行加入資料表或圖表這類的工作。 根據預設，鍵盤快速鍵對應為 Visual Studio 對應。 若要改用 Office 鍵盤快速鍵對應，請在 [ **工具** ] 功能表的 [ **選項** ] 對話方塊中，變更 [ **Microsoft Office 鍵盤設定** ] 節點下的設定。

### <a name="controls-on-documents"></a>文件上的控制項
 您可以將「 *主控制項* 」(Host Control) 和 Windows Forms 控制項，從 Visual Studio [ **工具箱** ] 拖曳至文件設計介面。 主控制項是 Office 物件 (例如 Word 內容控制項和 Excel 範圍) 的特製化版本，可用在以 Visual Studio 建立的 Office 專案中。 主控制項具有對應 Office 物件沒有的額外功能 (例如資料繫結和其他事件)。

 如需詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md) 和 [Office 檔上的 Windows forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)。

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>設計工具中的 Excel 工作表和活頁簿
 當您以設計工具開啟工作表時，修改工作表的方式與直接在 Excel 中開啟該工作表時相同。 如果您按兩下工作表儲存格，該儲存格會變更為編輯模式。 如果您按兩下包含主控制項的資料格，[程式碼編輯器] 隨即開啟，Visual Studio 產生控制項的預設事件處理常式。 若要巡覽至其他工作表，您可以按一下設計工具底端的工作表索引標籤。

 當您使用設計工具開啟活頁簿時，不會有任何設計介面。 活頁簿的設計檢視是一個填滿設計工具的大型元件匣。

 活頁簿和其內的每張工作表都有相關聯的程式碼檔。 每個程式碼檔都包含一個產生的「 *主項目* 」(Host Item) 類別，這個類別代表活頁簿或工作表。 如需詳細資訊，請參閱 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)。

### <a name="word-documents-in-the-designer"></a>設計工具中的 Word 檔
 當您使用設計工具開啟文件時，修改文件的方式與直接在 Word 中開啟該文件時相同。 如果您按兩下文件中的某個文字，便會選取該文字。 不過，如果該文字是在主控制項內，則會開啟程式碼編輯器，而 Visual Studio 會產生該控制項的預設事件處理常式。

 文件會具有相關聯的程式碼檔。 程式碼檔會包含一個產生的「 *主項目* 」(Host Item) 類別，這個類別代表文件。 如需詳細資訊，請參閱 [檔主專案](../vsto/document-host-item.md)。

### <a name="design-mode-vs-runtime-mode"></a>設計模式與執行時間模式的比較
 在 Visual Studio 環境中開啟文件時，文件一律會處於「 *設計模式*」(Design Mode)。 有些工作 (例如將主控制項拖曳至文件介面) 只能在設計模式下執行。

 若要在執行時間 *模式* 中查看檔，您必須在 Visual Studio 外部開啟應用程式和檔。 您也可以建置並執行專案，使其自動在 Visual Studio 外部開啟文件和應用程式。

## <a name="code-editor"></a>程式碼編輯器
 [程式碼編輯器] 可讓您檢視和修改方案中的可見程式碼檔。 這些檔案包含定義您方案行為的程式碼。

 如需程式碼編輯器的詳細資訊，請參閱在程式 [代碼和文字編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md)。 如需如何在 Office 專案中撰寫程式碼的詳細資訊，請參閱 [在 office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)。

## <a name="properties-window"></a>屬性視窗
 [ **屬性** ] 視窗會針對 [ **方案總管**] 中選取的專案項目，以及設計工具中選取的 UI 項目 (例如文件層級專案中的控制項或文件) 時，顯示項目的屬性。 有些屬性是特定於應用程式和文件的屬性，有些屬性則在所有的專案中都是相同的。

## <a name="data-sources-window"></a>資料來源視窗
 您可以使用文件層級 Office 專案中的 [ **資料來源** ] 視窗，將資料來源拖曳至您的文件，並建立繫結至資料來源的控制項。 如需詳細資訊，請參閱 [將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Office 專案範本總覽](../vsto/office-project-templates-overview.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office 專案中的屬性](../vsto/properties-in-office-projects.md)
