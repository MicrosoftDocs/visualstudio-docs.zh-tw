---
title: "格式、C#、文字編輯器、選項 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18cf7c7ee9c7f40231482b7c0466929bd0290fb1
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2017
---
# <a name="options-text-editor-c-formatting"></a>格式、C#、文字編輯器、選項
使用 [格式] 屬性頁對話方塊，設定程式碼編輯器中的程式碼格式化選項。 若要存取這個對話方塊，請按一下 [工具] 功能表上的 [選項]，並依序展開 [文字編輯器] 和 [C#]，然後按一下 [格式化]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="general-settings"></a>一般設定  
 一般設定會影響程式碼編輯器將格式化選項套用至程式碼的方式。  
  
## <a name="uielement-list"></a>UIElement 清單  
  
|ThisAddIn|說明|  
|-----------|-----------------|  
|**遇到 ; 字元時自動格式化完成的陳述式**|選取時，系統會在陳述式完成時，根據程式碼編輯器選取的格式化選項來格式化陳述式。 如果您不希望程式碼編輯器修改陳述式，請清除此方塊。|  
|**遇到 } 字元時自動格式化完成的區塊**|選取時，系統會在您完成程式碼區塊時，根據程式碼編輯器選取的格式化選項來格式化程式碼區塊。 如果您不希望程式碼編輯器修改區塊，請清除此方塊。|  
|**貼上時調整縮排**|選取時，系統會格式化貼入程式碼編輯器的文字，以符合程式碼編輯器選取的格式化選項。 如果您不希望系統修改貼上的文字，請清除此方塊。|  
  
## <a name="preview-window"></a>預覽視窗  
 [縮排]、[新行]、[間距] 和 [換行] 選項窗格都會顯示預覽視窗。 預覽視窗會呈現每個選項的效果。 若要使用預覽視窗，請選取一個格式化選項。 預覽視窗會呈現所選選項的範例。 當您變更設定時 (例如選取或清除核取方塊)，預覽視窗會更新以顯示新設定的效果。  
  
## <a name="remarks"></a>備註  
 針對每種語言，[索引標籤] 頁面上的 [縮排] 選項只會決定當您在結尾行按下 ENTER 時，程式碼編輯器會在哪裡放置游標。 [格式] 下方的 [縮排] 選項會在自動格式化程式碼時套用，例如：當您將程式碼貼入至檔案，同時選取 [貼上時調整縮排] 時，以及以手動方式輸入要格式化的區塊時。  
  
## <a name="see-also"></a>另請參閱  
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)