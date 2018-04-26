---
title: 格式、C#、文字編輯器、選項
ms.date: 02/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 534460d0ad6b7290190a88b3714c7f1eb0972723
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-c-formatting"></a>格式、C#、文字編輯器、選項

使用 [格式化] 選項頁面，可設定在程式碼編輯器中用於程式碼格式化的選項。 若要存取此選項頁面，請選擇 [工具] > [選項]，然後選擇 [文字編輯器] > [C#] > [程式碼樣式] > [格式化]。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="general-settings"></a>一般設定

一般設定會影響程式碼編輯器將格式化選項套用至程式碼的方式。

## <a name="uielement-list"></a>UIElement 清單

|ThisAddIn|描述|
|-----------|-----------------|
|**於輸入時自動格式化**|當取消選取時，會停用 [輸入 ; 時將陳述式格式化] 及 [輸入 } 時將區塊格式化] 選項。|
|**於 ; 處將陳述式自動格式化**|選取時，系統會在陳述式完成時，根據編輯器選取的格式化選項來將陳述式格式化。|
|**於 } 處將區塊自動格式化**|選取時，系統會在您完成程式碼區塊時，根據編輯器選取的格式化選項來將程式碼區塊格式化。|
|**在傳回時自動格式化**|選取時，會在按下 **Enter** 時將文字格式化，使其符合為編輯器選取的格式化選項。|
|**貼上時自動格式化**|選取時，系統會將貼入編輯器的文字格式化，使其符合為編輯器選取的格式化選項。|

## <a name="preview-window"></a>預覽視窗

[縮排]、[新行]、[間距] 和 [換行] 選項窗格都會顯示預覽視窗。 預覽視窗會呈現每個選項的效果。 若要使用預覽視窗，請選取一個格式化選項。 預覽視窗會呈現所選選項的範例。 當您選取選項按鈕或核取方塊以變更設定時，預覽視窗會更新以顯示新設定的影響。

## <a name="remarks"></a>備註

針對每種語言，[索引標籤] 頁面上的縮排選項只會決定當您在行末按下 **Enter** 時，程式碼編輯器會在哪裡放置游標。 [格式化] 下方的 [縮排] 選項會在自動格式化程式碼時套用，例如：當您將程式碼貼入至檔案，同時選取 [貼上時自動格式化] 時，以及以手動方式輸入要格式化的區塊時。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
