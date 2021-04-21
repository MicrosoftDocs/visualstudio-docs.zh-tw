---
title: 如何：使用內容控制項保護檔的元件
description: 瞭解如何使用 Visual Studio 來保護 Microsoft Word 檔的元件，方法是使用內容控制項。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc333871d4f371530db84a0c4f07ab891db2a937
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825468"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>如何：使用內容控制項保護檔的元件
  當您保護文件的某個部分時，使用者即無法變更或刪除文件中該部分的內容。 您可使用多種方法，透過內容控制項來保護 Microsoft Office Word 文件的下列部分：

- 您可以保護內容控制項。

- 您可以保護文件中不在內容控制項內的部分。

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> 保護內容控制項
 您可以透過文件層級專案，於設計階段或執行階段設定該控制項的屬性，以防止使用者編輯或刪除內容控制項。

 此外，您也可以使用 VSTO 增益集專案，保護於執行階段加入文件的內容控制項。 如需詳細資訊，請參閱 [如何：將內容控制項加入 Word 檔](../vsto/how-to-add-content-controls-to-word-documents.md)。

### <a name="to-protect-a-content-control-at-design-time"></a>若要在設計階段保護內容控制項

1. 在裝載於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 設計工具的文件中，選取想要保護的內容控制項。

2. 在 [ **屬性** ] 視窗中，設定下列其中一個或兩個屬性：

    - 若要防止使用者編輯控制項，請將 **LockContents** 設定為 **True**。

    - 若要防止使用者刪除控制項，請將 **LockContentControl** 設定為 **True**。

3. 按一下 [確定]  。

### <a name="to-protect-a-content-control-at-run-time"></a>若要在執行階段保護內容控制項

1. 將 `LockContents` 內容控制項的屬性設定為 **true** 以防止使用者編輯控制項，並將 `LockContentControl` 屬性設為 **true** ，以防止使用者刪除控制項。

     下列程式碼範例示範在文件層級專案中，使用兩個不同 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 物件的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> 和 <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> 屬性。 若要執行這個程式碼，請將程式碼加入專案的 `ThisDocument` 類別中，並從 `AddProtectedContentControls` 事件處理常式呼叫 `ThisDocument_Startup` 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet2":::

     下列程式碼範例示範在 VSTO 增益集專案中，使用兩個不同 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 物件的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> 和 <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> 屬性。 若要執行這個程式碼，請將程式碼加入專案的 `ThisAddIn` 類別中，並從 `AddProtectedContentControls` 事件處理常式呼叫 `ThisAddIn_Startup` 方法。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet14":::

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>保護檔中不在內容控制項內的部分
 您可以將文件區域放入 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 中，防止使用者變更該區域。 這在下列案例中很有用：

- 您想要保護不含內容控制項的區域。

- 您想要保護已包含內容控制項的區域，但是想要保護的文字或其他項目不在內容控制項內。

> [!NOTE]
> 如果建立的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 包含內嵌內容控制項，則不會自動保護這些內嵌內容控制項。 若要防止使用者編輯內嵌的內容控制項，請使用控制項的 **LockContents** 屬性。

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>若要在設計階段保護文件的區域

1. 在裝載於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 設計工具的文件中，選取想要保護的區域。

2. 按一下 [功能區] 上的 [開發人員]  索引標籤。

    > [!NOTE]
    > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

3. 在 [ **控制項** ] 群組中，按一下 [ **群組** ] 下拉按鈕，然後按一下 [ **群組**]。

     這樣會在專案的 `ThisDocument` 類別中，自動產生內含保護區域的 <xref:Microsoft.Office.Tools.Word.GroupContentControl>。 在設計階段可以看到代表群組控制項的框線，但是在執行階段則看不到框線。

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>若要在執行階段保護文件的區域

1. 以程式設計方式選取想要保護的區域，然後呼叫 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> 方法以建立 <xref:Microsoft.Office.Tools.Word.GroupContentControl>。

     下列文件層級專案的程式碼範例會將文字加入文件的第一個段落，然後選取此段落，再執行個體化 <xref:Microsoft.Office.Tools.Word.GroupContentControl>。 若要執行這個程式碼，請將程式碼加入專案的 `ThisDocument` 類別中，並從 `ProtectFirstParagraph` 事件處理常式呼叫 `ThisDocument_Startup` 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet1":::

     下列 VSTO 增益集專案的程式碼範例會將文字加入使用中文件的第一個段落，然後選取此段落，再執行個體化 <xref:Microsoft.Office.Tools.Word.GroupContentControl>。 若要執行這個程式碼，請將程式碼加入專案的 `ThisAddIn` 類別中，並從 `ProtectFirstParagraph` 事件處理常式呼叫 `ThisAddIn_Startup` 方法。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet15":::

## <a name="see-also"></a>另請參閱
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [內容控制項](../vsto/content-controls.md)
- [如何：將內容控制項新增至 Word 檔](../vsto/how-to-add-content-controls-to-word-documents.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
