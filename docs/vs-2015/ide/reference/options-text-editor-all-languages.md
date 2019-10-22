---
title: 選項、文字編輯器、所有語言 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662407"
---
# <a name="options-text-editor-all-languages"></a>選項，文字編輯器，所有語言
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

編輯樣式表時，這個對話方塊可讓您變更程式碼編輯器的預設行為。 這些設定也適用於以程式碼編輯器為基礎的其他編輯器，例如 HTML 設計工具的來源檢視。 若要開啟此對話方塊，請從 [工具]  功能表選取 [選項]  。 在 [文字編輯器]  資料夾內，展開 [所有語言]  子資料夾，然後選擇 [一般]  。

> [!CAUTION]
> 此頁面會設定所有開發語言的預設選項。 請記住，重設此對話方塊中的選項，會將所有語言中的 [一般] 選項重設為此處所選的選項。 若只要變更單一語言的文字編輯器選項，請展開該語言的子資料夾，然後選取其選項頁面。

 當某些程式設計語言的 [一般] 選項頁面上已經選取某個選項，但其他程式設計語言尚未選取時，會顯示呈現灰色的核取記號。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

## <a name="statement-completion"></a>陳述式完成
 當選取 [自動列出成員] 時，IntelliSense 會在您于編輯器中輸入時，顯示可用成員、屬性、值或方法的快顯清單。 選擇快顯清單中的任何項目，以將項目插入您的程式碼。 選取此選項可啟用 [隱藏進階成員]  選項。

 選取時隱藏 advanced 成員，只顯示最常使用的專案，以縮短快顯語句完成清單。 會篩選清單中的其他項目。

 參數資訊選取時，會在編輯器中的插入點底下顯示目前宣告或程式的完整語法，以及所有可用的參數。 可以指派的下一個參數以粗體顯示。

## <a name="settings"></a>設定
 啟用 [虛擬空間] 當選取此選項並清除 [**自動換**行] 時，您可以按一下程式碼編輯器中一行結尾以外的任何位置，然後輸入。 這個功能可以用來將註解放置在程式碼旁邊的一致位置上。

 選取 [自動換行] 時，以水準方式延伸到 [可見編輯器] 區域外的線條的任何部分都會自動顯示在下一行。 選取這個選項，會啟用 [顯示自動換行的視覺化圖像]  選項。

> [!NOTE]
> 開啟 [自動換行]  時，[虛擬空間]  功能會關閉。

 [顯示自動換行的視覺效果圖像] 選取時，會在長行換行至另一行時顯示傳回箭號指標。

 ![LineBreakSymbol 螢幕擷取畫面](../../ide/reference/media/linebreak.gif "linebreak")

 如果您不想顯示這些指示器，請清除這個選項。

> [!NOTE]
> 這些提醒箭號不會加入至程式碼，也不會列印。 僅供參考之用。

 當沒有選取專案時，將 [剪下] 或 [複製] 命令套用至空白行：當您將插入點放置在空白行上、不選取任何內容，然後按一下 [複製] 或 [剪下] 時，此選項會設定編輯器的行為。

- 選取這個選項時，即可複製或剪下這個空白行。 如果您稍後貼上，則會插入新的空白行。

- 清除此選項時，則「剪下」命令會移除空白行。 不過，會保留剪貼簿裡的資料。 因此，如果您稍後使用 [貼上] 命令，則會貼上最近複製到剪貼簿的內容。 如果先前沒有複製任何項目，則不會貼上任何內容。

  某行不是空白行時，這個設定對複製或剪下沒有作用。 如果沒有選取任何範圍，則會複製或剪下整行。 如果您稍後貼上，則會貼上整行的文字及其行尾字元。

> [!TIP]
> 若要顯示空格、定位點和行尾的指示器，並進而區分縮排行與完全空白的行，請從 [編輯]  功能表選取 [進階]  ，並選擇 [檢視空格]  。

## <a name="display"></a>顯示
 行號選取時，會在每一行程式碼旁邊顯示行號。

> [!NOTE]
> 這些行號不會新增至您的程式碼，也不會列印。 僅供參考之用。

 啟用單鍵 URL 導覽選取時，當滑鼠游標在編輯器中通過 URL 時，就會變更為手形。 您可以按一下 URL，在 Web 瀏覽器中顯示手形指標所指示的網頁。

 選取 [導覽列] 時，會在程式碼編輯器的頂端顯示**巡覽列**。 它的下拉式 [物件]  和 [成員]  清單，可讓您選擇程式碼中的特定物件、從其成員選擇，並在程式碼編輯器中巡覽至選取之成員的宣告。

## <a name="see-also"></a>另請參閱
 [使用 IntelliSense](../../ide/using-intellisense.md)的[選項、文字編輯器、所有語言、](../../ide/reference/options-text-editor-all-languages-tabs.md)索引標籤[一般、環境、選項對話方塊](../../ide/reference/general-environment-options-dialog-box.md)
