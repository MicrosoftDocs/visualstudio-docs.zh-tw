---
title: 選項，文字編輯器，所有語言
description: 瞭解如何使用 [所有語言] 區段中的 [一般] 頁面，在 Visual Studio 中變更程式碼編輯器的預設行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b507f79aa4afb1bd5d2f56893d2e32aae0db4c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905577"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>選項對話方塊：文字編輯器 \> 所有語言

編輯樣式表時，這個對話方塊可讓您變更程式碼編輯器的預設行為。 這些設定也適用於以程式碼編輯器為基礎的其他編輯器，例如 HTML 設計工具的來源檢視。 若要開啟此對話方塊，請從 [工具] 功能表選取 [選項]。 在 [文字編輯器] 資料夾內，展開 [所有語言] 子資料夾，然後選擇 [一般]。

> [!CAUTION]
> 此頁面會設定所有開發語言的預設選項。 請記住，重設此對話方塊中的選項，會將所有語言中的 [一般] 選項重設為此處所選的選項。 若只要變更單一語言的文字編輯器選項，請展開該語言的子資料夾，然後選取其選項頁面。

當某些程式設計語言的 [一般] 選項頁面上已經選取某個選項，但其他程式設計語言尚未選取時，會顯示呈現灰色的核取記號。

## <a name="statement-completion"></a>陳述式完成

**自動列出成員**

選取時，IntelliSense 會在您於編輯器中輸入時，顯示可用成員、屬性、值或方法的快顯清單。 從快顯清單中選擇任何項目，以將項目插入程式碼。 選取此選項可啟用 [隱藏進階成員] 選項。

**隱藏進階成員**

選取時，會縮短快顯陳述式完成清單，只顯示最常用的項目。 從清單中篩選其他項目。

**參數資訊**

選取時，編輯器中插入點之下會顯示目前宣告或程序的完整語法，以及所有的可用參數。 您可以指派的下一個參數會以粗體顯示。

## <a name="settings"></a>設定

**啟用虛擬空間**

選取這個選項，並清除 [自動換行] 時，您可以在 [程式碼編輯器] 中，按一下行尾之外的任何位置，然後輸入內容。 這個功能可以用來將註解放置在程式碼旁邊的一致位置上。

**自動換行**

選取時，如果某行的水平延伸部分超過可檢視的編輯器區域，超過的部分會自動顯示於下一行。 選取這個選項，會啟用 [顯示自動換行的視覺化圖像] 選項。

> [!NOTE]
> 開啟 [自動換行] 時，[虛擬空間] 功能會關閉。

**顯示自動換行的視覺化圖像**

選取時，會在長行換行至下一行之處顯示返回箭號指標。

![LineBreakSymbol 螢幕擷取畫面](../../ide/reference/media/linebreak.gif)

如果您不想顯示這些指示器，請清除這個選項。

> [!NOTE]
> 這些提醒箭號不會加入至程式碼，也不會列印。 它們僅供參考。

**行號**

選取時，會在每一行程式碼旁邊顯示行號。

> [!NOTE]
> 這些行號不會新增至您的程式碼，也不會列印。 它們僅供參考。

**啟用按一下方式的 URL 導覽**

選取此選項，且滑鼠游標經過編輯器的 URL 上方時，就會變為指示手形狀。 您可以按一下 URL，在網頁瀏覽器中顯示手形指標所指示的網頁。

**導覽列**

選取時，會在程式碼編輯器的頂端顯示 [導覽列]。 它的下拉式 [物件] 和 [成員] 清單，可讓您選擇程式碼中的特定物件、從其成員選擇，並在程式碼編輯器中巡覽至選取之成員的宣告。

**沒有選取範圍時，可將 [剪下] 或 [複製] 命令套用至空白行**

當您將插入點置於空白行上但不選取任何範圍，然後「複製」或「剪下」時，這個選項可設定編輯器的行為。

- 選取這個選項時，即可複製或剪下這個空白行。 如果您稍後貼上，則會插入新的空白行。

- 清除此選項時，則「剪下」命令會移除空白行。 不過，會保留剪貼簿裡的資料。 因此，如果您稍後使用 [貼上] 命令，則會貼上最近複製到剪貼簿的內容。 如果先前沒有進行複製，就不會有貼上動作。

某行不是空白行時，這個設定對複製或剪下沒有作用。 如果沒有選取內容，就會複製或剪下整個行。 如果您稍後貼上，則會貼上整行的文字及其行尾字元。

> [!TIP]
> 若要顯示空格、定位點和行尾的指示器，並進而區分縮排行與完全空白的行，請從 [編輯] 功能表選取 [進階]，並選擇 [檢視空格]。

## <a name="see-also"></a>另請參閱

- [索引標籤、所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
- [使用 IntelliSense](../../ide/using-intellisense.md)
