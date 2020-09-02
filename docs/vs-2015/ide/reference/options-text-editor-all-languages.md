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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662407"
---
# <a name="options-text-editor-all-languages"></a>選項，文字編輯器，所有語言
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

編輯樣式表時，這個對話方塊可讓您變更程式碼編輯器的預設行為。 這些設定也適用於以程式碼編輯器為基礎的其他編輯器，例如 HTML 設計工具的來源檢視。 若要開啟此對話方塊，請從 [工具]**** 功能表選取 [選項]****。 在 [文字編輯器]**** 資料夾內，展開 [所有語言]**** 子資料夾，然後選擇 [一般]****。

> [!CAUTION]
> 此頁面會設定所有開發語言的預設選項。 請記住，重設此對話方塊中的選項，會將所有語言中的 [一般] 選項重設為此處所選的選項。 若只要變更單一語言的文字編輯器選項，請展開該語言的子資料夾，然後選取其選項頁面。

 當某些程式設計語言的 [一般] 選項頁面上已經選取某個選項，但其他程式設計語言尚未選取時，會顯示呈現灰色的核取記號。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="statement-completion"></a>陳述式完成
 當您在編輯器中輸入時，IntelliSense 會顯示已選取的自動清單成員、可用成員、屬性、值或方法的快顯清單。 從快顯清單中選擇任何項目，以將項目插入程式碼。 選取此選項可啟用 [隱藏進階成員]**** 選項。

 在選取時隱藏 advanced members，藉由只顯示最常使用的專案，縮短彈出語句完成清單。 從清單中篩選其他項目。

 參數資訊：選取時，目前宣告或程式的完整語法會顯示在編輯器中的插入點下，以及所有可用的參數。 您可以指派的下一個參數會以粗體顯示。

## <a name="settings"></a>設定
 當選取這個選項且清除 **自動換** 行時，您可以在程式碼編輯器中，按一下行尾之外的任何位置，然後輸入，即可啟用 [虛擬空間]。 這個功能可以用來將註解放置在程式碼旁邊的一致位置上。

 選取 [自動換行] 時，以水準方式延伸至可見編輯器區域以外之線條的任何部分都會自動顯示在下一行。 選取這個選項，會啟用 [顯示自動換行的視覺化圖像]**** 選項。

> [!NOTE]
> 開啟 [自動換行]**** 時，[虛擬空間]**** 功能會關閉。

 當選取時，顯示自動換行的視覺化圖像，當長行換行到第二行時，會顯示傳回箭號指標。

 ![LineBreakSymbol 螢幕擷取畫面](../../ide/reference/media/linebreak.gif "linebreak")

 如果您不想顯示這些指示器，請清除這個選項。

> [!NOTE]
> 這些提醒箭號不會加入至程式碼，也不會列印。 它們僅供參考。

 當沒有選取專案時，將剪下或複製命令套用至空白行：當您將插入點放在空白行上、不選取任何內容，然後複製或剪下時，會設定編輯器的行為。

- 選取這個選項時，即可複製或剪下這個空白行。 如果您稍後貼上，則會插入新的空白行。

- 清除此選項時，則「剪下」命令會移除空白行。 不過，會保留剪貼簿裡的資料。 因此，如果您稍後使用 [貼上] 命令，則會貼上最近複製到剪貼簿的內容。 如果先前沒有進行複製，就不會有貼上動作。

  某行不是空白行時，這個設定對複製或剪下沒有作用。 如果沒有選取內容，就會複製或剪下整個行。 如果您稍後貼上，則會貼上整行的文字及其行尾字元。

> [!TIP]
> 若要顯示空格、定位點和行尾的指示器，並進而區分縮排行與完全空白的行，請從 [編輯]**** 功能表選取 [進階]****，並選擇 [檢視空格]****。

## <a name="display"></a>顯示
 選取行號時，行號會出現在每一行程式碼旁邊。

> [!NOTE]
> 這些行號不會新增至您的程式碼，也不會列印。 它們僅供參考。

 當選取時，請啟用單鍵 URL 流覽，當滑鼠游標在編輯器中的 URL 上通過時，滑鼠游標會變更為手形。 按一下 URL 即可在 Web 瀏覽器中顯示該頁面。

 選取此選項時，會在程式碼編輯器頂端顯示 **導航** 欄。 它的下拉式 [物件]**** 和 [成員]**** 清單，可讓您選擇程式碼中的特定物件、從其成員選擇，並在程式碼編輯器中巡覽至選取之成員的宣告。

## <a name="see-also"></a>另請參閱
 [使用 IntelliSense](../../ide/using-intellisense.md)的[選項、文字編輯器、所有語言、](../../ide/reference/options-text-editor-all-languages-tabs.md)索引標籤[一般、環境、選項對話方塊](../../ide/reference/general-environment-options-dialog-box.md)
