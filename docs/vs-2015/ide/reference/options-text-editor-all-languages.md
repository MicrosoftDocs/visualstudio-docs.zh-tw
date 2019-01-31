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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0abb0a38e63231dfddea391b3a63a73ae982bd24
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802554"
---
# <a name="options-text-editor-all-languages"></a>選項，文字編輯器，所有語言
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
編輯樣式表時，這個對話方塊可讓您變更程式碼編輯器的預設行為。 這些設定也適用於以程式碼編輯器為基礎的其他編輯器，例如 HTML 設計工具的來源檢視。 若要開啟此對話方塊，請從 [工具] 功能表選取 [選項]。 在 [文字編輯器] 資料夾內，展開 [所有語言] 子資料夾，然後選擇 [一般]。  
  
> [!CAUTION]
>  此頁面會設定所有開發語言的預設選項。 請記住，重設此對話方塊中的選項，會將所有語言中的 [一般] 選項重設為此處所選的選項。 若只要變更單一語言的文字編輯器選項，請展開該語言的子資料夾，然後選取其選項頁面。  
  
 當某些程式設計語言的 [一般] 選項頁面上已經選取某個選項，但其他程式設計語言尚未選取時，會顯示呈現灰色的核取記號。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="statement-completion"></a>陳述式完成  
 自動列出成員  
 選取時，IntelliSense 會在您於編輯器中輸入時，顯示可用成員、屬性、值或方法的快顯清單。 選擇快顯清單中的任何項目，以將項目插入您的程式碼。 選取此選項可啟用 [隱藏進階成員] 選項。  
  
 隱藏進階成員  
 選取時，會縮短快顯陳述式完成清單，只顯示最常用的項目。 會篩選清單中的其他項目。  
  
 參數資訊  
 選取時，編輯器中插入點之下會顯示目前宣告或程序的完整語法，以及所有的可用參數。 可以指派的下一個參數以粗體顯示。  
  
## <a name="settings"></a>設定  
 啟用虛擬空間  
 選取這個選項，並清除 [自動換行] 時，您可以在 [程式碼編輯器] 中，按一下行尾之外的任何位置，然後輸入內容。 這個功能可以用來將註解放置在程式碼旁邊的一致位置上。  
  
 自動換行  
 選取時，如果某行的水平延伸部分超過可檢視的編輯器區域，超過的部分會自動顯示於下一行。 選取這個選項，會啟用 [顯示自動換行的視覺化圖像] 選項。  
  
> [!NOTE]
>  開啟 [自動換行] 時，[虛擬空間] 功能會關閉。  
  
 顯示自動換行的視覺化圖像  
 選取時，會在長行換行至下一行之處顯示返回箭號指標。  
  
 ![LineBreakSymbol 螢幕擷取畫面](../../ide/reference/media/linebreak.gif "linebreak")  
  
 如果您不想顯示這些指示器，請清除這個選項。  
  
> [!NOTE]
>  這些提醒箭號不會加入至程式碼，也不會列印。 僅供參考之用。  
  
 沒有選取範圍時，可將 [剪下] 或 [複製] 命令套用至空白行  
 當您將插入點置於空白行上但不選取任何範圍，然後「複製」或「剪下」時，這個選項可設定編輯器的行為。  
  
- 選取這個選項時，即可複製或剪下這個空白行。 如果您稍後貼上，則會插入新的空白行。  
  
- 清除此選項時，則「剪下」命令會移除空白行。 不過，會保留剪貼簿裡的資料。 因此，如果您稍後使用 [貼上] 命令，則會貼上最近複製到剪貼簿的內容。 如果先前沒有複製任何項目，則不會貼上任何內容。  
  
  某行不是空白行時，這個設定對複製或剪下沒有作用。 如果沒有選取任何範圍，則會複製或剪下整行。 如果您稍後貼上，則會貼上整行的文字及其行尾字元。  
  
> [!TIP]
>  若要顯示空格、定位點和行尾的指示器，並進而區分縮排行與完全空白的行，請從 [編輯] 功能表選取 [進階]，並選擇 [檢視空格]。  
  
## <a name="display"></a>顯示  
 行號  
 選取時，會在每一行程式碼旁邊顯示行號。  
  
> [!NOTE]
>  這些行號不會新增至您的程式碼，也不會列印。 僅供參考之用。  
  
 啟用按一下方式的 URL 巡覽  
 選取此選項，且滑鼠游標經過編輯器的 URL 上方時，就會變為指示手形狀。 您可以按一下 URL，在 Web 瀏覽器中顯示手形指標所指示的網頁。  
  
 巡覽列  
 選取時，會在程式碼編輯器的頂端顯示 [導覽列]。 它的下拉式 [物件] 和 [成員] 清單，可讓您選擇程式碼中的特定物件、從其成員選擇，並在程式碼編輯器中巡覽至選取之成員的宣告。  
  
## <a name="see-also"></a>請參閱  
 [選項、文字編輯器、所有語言、定位點](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)
