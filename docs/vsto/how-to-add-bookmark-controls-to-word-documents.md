---
title: HOW TO：將書籤控制項加入 Word 文件
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7948af3a6a77fd100a6965f9e50cda70ac7b868d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427777"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>HOW TO：將書籤控制項加入 Word 文件
  在文件層級專案中，您可以新增<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入文件，在您的專案，在設計階段或執行階段。 在 VSTO 增益集專案中，您可以新增<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入任何開啟的文件，在執行階段。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 本主題說明下列工作：

- [在設計階段加入書籤控制項](#designtime)

- [在文件層級專案中的執行階段加入書籤控制項](#runtimedoclevel)

- [在 VSTO 增益集專案中的執行階段加入書籤控制項](#runtimeaddin)

  如需詳細資訊<xref:Microsoft.Office.Tools.Word.Bookmark>控制項，請參閱[書籤控制項](../vsto/bookmark-control.md)。

## <a name="designtime"></a> 在設計階段加入書籤控制項
 在文件層級專案的設計階段，有數種方式可將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入文件：

- 從 Visual Studio [工具箱] 。

   您可以從 [工具箱] <xref:Microsoft.Office.Tools.Word.Bookmark>**將** 控制項拖曳至文件。 如果您已經使用 [工具箱]  將 Windows Form 控制項加入文件，您可能會想要選擇這種方式。

- 從 Word 內部。

   您可以用加入原生書籤的方式，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入文件。 用這種方式加入控制項的優點，是您可以在建立控制項時為其命名。

- 從 [資料來源]  視窗。

   您可以從 [資料來源] <xref:Microsoft.Office.Tools.Word.Bookmark>**視窗將** 控制項拖曳至文件。 當您想要在同一時間將控制項繫結至資料時，這會很有用。 您可以用加入 Windows Form 控制項的方式，從 [資料來源]  視窗加入主控制項。 如需詳細資訊，請參閱 <<c0> [ 資料繫結和 Windows Form](/dotnet/framework/winforms/data-binding-and-windows-forms)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>從 [工具箱] 將書籤控制項加入文件

1. 開啟 [工具箱]  ，然後按一下 [Word 控制項]  索引標籤。

2. 將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項拖曳至文件。

     [加入書籤]  對話方塊隨即出現。

3. 選取您想要包含在書籤內的文字或其他項目。

4. 按一下 [確定] 。

     如果您不想保留預設的書籤名稱，您可以在 [屬性]  視窗中變更名稱。

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>在 Word 文件中加入書籤控制項

1. 在裝載於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 設計工具的文件中，將游標放在您要加入書籤的位置，或選取您希望放在書籤中的文字。

2. 在功能區的 [插入]  索引標籤中，按一下 [連結]  群組中的 [書籤]  按鈕。

3. 在 [書籤]  對話方塊中，輸入新書籤的名稱，然後按一下 [加入] 。

## <a name="runtimedoclevel"></a> 在文件層級專案中的執行階段加入書籤控制項
 您可以加入<xref:Microsoft.Office.Tools.Word.Bookmark>所使用的方法以程式設計方式控制您的文件，在執行階段<xref:Microsoft.Office.Tools.Word.Document.Controls%2A>屬性`ThisDocument`專案中的類別。 有兩種方法多載可用來以下列方法加入 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項：

- 在指定的範圍加入 <xref:Microsoft.Office.Tools.Word.Bookmark>

- 加入以文件原生書籤為基礎的 <xref:Microsoft.Office.Tools.Word.Bookmark> (也就是 <xref:Microsoft.Office.Interop.Word.Bookmark>)。

  文件關閉後，不會保存動態建立的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。 不過，原生的 <xref:Microsoft.Office.Interop.Word.Bookmark> 會保留在文件中。 下次開啟文件時，您可以重新建立以原生書籤為基礎的 <xref:Microsoft.Office.Tools.Word.Bookmark> 。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>以程式設計的方式在文件中加入書籤控制項

1. 在專案的 `ThisDocument_Startup` 事件處理常式中，插入下列程式碼，在文件的第一個段落加入 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。

     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]

    > [!NOTE]
    > 如果您想要從現有的 <xref:Microsoft.Office.Tools.Word.Bookmark> 建立 <xref:Microsoft.Office.Interop.Word.Bookmark>控制項，請使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 方法並傳入現有的 <xref:Microsoft.Office.Interop.Word.Bookmark>。

## <a name="runtimeaddin"></a> 在 VSTO 增益集專案中的執行階段加入書籤控制項
 您可以新增<xref:Microsoft.Office.Tools.Word.Bookmark>控制項以程式設計方式加入任何開啟的文件，在執行階段使用 VSTO 增益集。 若要這麼做，請產生以開啟文件為基礎的 <xref:Microsoft.Office.Tools.Word.Document> 主項目，然後使用這個主項目之 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性的方法。 有兩種方法多載可用來以下列方法加入 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項：

- 在指定的範圍加入 <xref:Microsoft.Office.Tools.Word.Bookmark>

- 加入以文件原生書籤為基礎的 <xref:Microsoft.Office.Tools.Word.Bookmark> (也就是 <xref:Microsoft.Office.Interop.Word.Bookmark>)。

  文件關閉後，不會保存動態建立的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。 不過，原生的 <xref:Microsoft.Office.Interop.Word.Bookmark> 會保留在文件中。 下次開啟文件時，您可以重新建立以原生書籤為基礎的 <xref:Microsoft.Office.Tools.Word.Bookmark> 。 如需詳細資訊，請參閱 <<c0> [ 保存動態控制項中的 Office 文件](../vsto/persisting-dynamic-controls-in-office-documents.md)。

  如需在 VSTO 增益集專案中產生主項目的詳細資訊，請參閱 <<c0> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>在指定的範圍加入書籤控制項

1. 使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 方法，並傳入想要加入 <xref:Microsoft.Office.Interop.Word.Range> 所在的 <xref:Microsoft.Office.Tools.Word.Bookmark>。

     下列程式碼範例會在使用中文件的開頭加入新的 <xref:Microsoft.Office.Tools.Word.Bookmark> 。 若要使用這個範例，請從 Word VSTO 增益集專案的 `ThisAddIn_Startup` 事件處理常式執行程式碼。

     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>加入以原生書籤控制項為基礎的書籤控制項

1. 使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 方法，並傳入您想要用做新 <xref:Microsoft.Office.Interop.Word.Bookmark> 之基礎的現有 <xref:Microsoft.Office.Tools.Word.Bookmark>。

     下列程式碼範例會根據使用中文件的第一個 <xref:Microsoft.Office.Tools.Word.Bookmark> 建立新的 <xref:Microsoft.Office.Interop.Word.Bookmark> 若要使用這個範例，請從 Word VSTO 增益集專案的 `ThisAddIn_Startup` 事件處理常式執行程式碼。

     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]

## <a name="see-also"></a>另請參閱
- [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [程式文件層級自訂](../vsto/programming-document-level-customizations.md)
- [如何：調整書籤控制項的大小](../vsto/how-to-resize-bookmark-controls.md)
