---
title: 格式、C#、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5371b7180aed462910a57daeb9bf5d43f2ecfedb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662279"
---
# <a name="options-text-editor-c-formatting"></a>格式、C#、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 [格式]**** 屬性頁對話方塊，設定程式碼編輯器中的程式碼格式化選項。 若要存取這個對話方塊，請按一下 [工具]**** 功能表上的 [選項]****，並依序展開 [文字編輯器]**** 和 [C#]****，然後按一下 [格式化]****。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="general-settings"></a>一般設定
 一般設定會影響程式碼編輯器將格式化選項套用至程式碼的方式。

## <a name="uielement-list"></a>UIElement 清單

|標籤|描述|
|-----------|-----------------|
|**遇到 ; 字元時自動格式化完成的陳述式**|選取時，系統會在陳述式完成時，根據程式碼編輯器選取的格式化選項來格式化陳述式。 如果您不希望程式碼編輯器修改陳述式，請清除此方塊。|
|**遇到 } 字元時自動格式化完成的區塊**|選取時，系統會在您完成程式碼區塊時，根據程式碼編輯器選取的格式化選項來格式化程式碼區塊。 如果您不希望程式碼編輯器修改區塊，請清除此方塊。|
|**貼上時調整縮排**|選取時，系統會格式化貼入程式碼編輯器的文字，以符合程式碼編輯器選取的格式化選項。 如果您不希望系統修改貼上的文字，請清除此方塊。|

## <a name="preview-window"></a>預覽視窗
 [縮排]****、[新行]****、[間距]**** 和 [換行]**** 選項窗格都會顯示預覽視窗。 預覽視窗會呈現每個選項的效果。 若要使用預覽視窗，請選取一個格式化選項。 預覽視窗會呈現所選選項的範例。 當您變更設定時 (例如選取或清除核取方塊)，預覽視窗會更新以顯示新設定的效果。

## <a name="remarks"></a>備註
 每種語言的索引卷 **標頁上** 的縮排選項只會決定當您在行尾按下 enter 時，程式碼編輯器放置游標的位置。 [格式]**** 下方的 [縮排] 選項會在自動格式化程式碼時套用，例如：當您將程式碼貼入至檔案，同時選取 [貼上時調整縮排]**** 時，以及以手動方式輸入要格式化的區塊時。

## <a name="see-also"></a>另請參閱
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
