---
title: 選項、文字編輯器、JavaScript、IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b3b17416902bac2bcc7ff03adc39e548e63fb229
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879354"
---
# <a name="options-text-editor-javascript-intellisense"></a>IntelliSense、JavaScript、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[選項、 文字編輯器、 JavaScript、 IntelliSense](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-javascript-intellisense)。  
  
  
使用 [ **選項** ] 對話方塊的 [ **IntelliSense** ] 頁面修改影響 JavaScript 之 IntelliSense 行為的設定。 您可以選擇功能表列上的 [ **工具** ]、[ **選項**, **文字編輯器** ]、[ **IntelliSense**, **IntelliSense**, **工具.**] 頁面。  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
 [ **IntelliSense** ] 頁面包含下列區段：  
  
## <a name="validation"></a>驗證  
 您可以使用這些選項設定 JavaScript 編輯器驗證文件中語法的偏好設定。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **顯示語法錯誤**  
 如果沒有選取這個核取方塊，JavaScript 程式碼編輯器就不會顯示任何語法錯誤。 如果您不是使用自己撰寫的程式碼，而且不想修改語法錯誤，這樣做會很實用。  
  
 選取這個核取方塊時，您還可以選擇選取 [ **將錯誤顯示為警告** ] 核取方塊。  
  
 **將錯誤顯示為警告**  
 選取這個核取方塊時，JavaScript 錯誤會顯示為警告而非錯誤清單中的錯誤。  
  
 **針對其他檔案專案中的檔案下載遠端參考 (例如 http://)**  
 當您選取這個核取方塊，而且在專案內容之外有開啟的 JavaScript 檔案，則 Visual Studio 會下載檔案中所參考的遠端 JavaScript 檔案，以便提供 IntelliSense 資訊。 如果已選取這個選項，檔案會在您將它們包含在 JavaScript 檔案中做為參考時下載。  
  
> [!NOTE]
>  Web 專案預設會下載專案中參考的遠端檔案。  
  
## <a name="statement-completion"></a>陳述式完成  
 您可以使用這些選項變更 IntelliSense 陳述式完成的行為。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **僅使用 Tab 或 Enter 進行認可**  
 選取這個核取方塊時，JavaScript 程式碼編輯器只會在您選擇 Tab 或 Enter 鍵之後，才將完成清單中選取的項目附加至陳述式。 未選取這個核取方塊時，其他字元像是句號、逗號、冒號、左括號和左大括號 ({) 也可以在陳述式中附加選取的項目。  
  
## <a name="references"></a>參考  
 您可以使用這些選項指定不同 JavaScript 專案類型範圍中 IntelliSense .js 檔案的類型。 IntelliSense 參考通常是用來為全域物件提供 IntelliSense 支援。 您也可以使用這個頁面設定必須在執行階段載入之指令碼的載入順序，以及加入 IntelliSense 擴充檔案。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **參考群組**  
 這個選項會指定參考群組類型。 支援的參考群組有三種：  
  
 您可以使用預先定義的參考群組指定特殊 IntelliSense .js 檔案於不同 JavaScript 專案範圍中。 有四種參考群組可用：  
  
-   隱含 (Windows *版本*)，適用於使用 JavaScript 的 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] 應用程式。 此群組中所含的檔案會在程式碼編輯器中針對使用 JavaScript 的 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] 應用程式開啟的每個 .js 檔案範圍中。  
  
-   隱含 (Web)，適用於 HTML5 專案。 這個群組中包含的檔案會在程式碼編輯器中針對這些專案類型開啟的每一個 .js 檔案範圍中。  
  
-   專屬的背景工作參考群組，適用於 HTML5 Web 背景工作。 在這個群組中指定的檔案會在具有專屬背景工作參考群組之明確參考的 .js 檔案範圍中。  
  
-   泛型，適用於其他 JavaScript 專案類型。  
  
 **包含的檔案**  
 這個選項會指定檔案載入語言服務內容的順序。 您可以使用 [ **移除**]、[ **上移**] 和 [ **下移** ] 按鈕設定順序。 若要讓 IntelliSense 正常運作，相依於另一個檔案的檔案必須在另一個檔案載入後才能載入。  
  
> [!CAUTION]
>  如果以不設條件的方式在兩個以上的隱含參考中定義物件，則這個清單中的最後一個參考將用來定義該物件。  
  
 **加入群組的參考**  
 這個選項可讓您透過瀏覽至適當檔案的方式，加入其他 IntelliSense .js 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)



