---
title: 選項、文字編輯器、JavaScript、IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b0d9dec8ec9b3eb8860bb8b3a4ed8f7347aa54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662238"
---
# <a name="options-text-editor-javascript-intellisense"></a>IntelliSense、JavaScript、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 [ **選項** ] 對話方塊的 [ **IntelliSense** ] 頁面修改影響 JavaScript 之 IntelliSense 行為的設定。 您可以選擇功能表列上的 [ **工具** ]、[ **選項**, **文字編輯器** ]、[ **IntelliSense**, **IntelliSense**, **工具.**] 頁面。

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 [ **IntelliSense** ] 頁面包含下列區段：

## <a name="validation"></a>驗證
 您可以使用這些選項設定 JavaScript 編輯器驗證文件中語法的偏好設定。

## <a name="uielement-list"></a>UIElement 清單
 **顯示語法錯誤** 如果未選取此核取方塊，JavaScript 程式碼編輯器就不會顯示語法錯誤。 如果您不是使用自己撰寫的程式碼，而且不想修改語法錯誤，這樣做會很實用。

 選取這個核取方塊時，您還可以選擇選取 [ **將錯誤顯示為警告** ] 核取方塊。

 將**錯誤顯示為警告**選取此核取方塊時，JavaScript 錯誤會顯示為警告，而不是錯誤清單中的錯誤。

 **針對其他檔案專案中的檔案下載遠端參考 (例如 HTTP://) ** 如果選取此核取方塊，而且您有在專案內容以外開啟的 JavaScript 檔案，Visual Studio 將會下載檔案中所參考的遠端 JavaScript 檔案，以便提供 IntelliSense 資訊。 如果已選取這個選項，檔案會在您將它們包含在 JavaScript 檔案中做為參考時下載。

> [!NOTE]
> Web 專案預設會下載專案中參考的遠端檔案。

## <a name="statement-completion"></a>陳述式完成
 您可以使用這些選項變更 IntelliSense 陳述式完成的行為。

## <a name="uielement-list"></a>UIElement 清單
 **只使用 tab 或 enter 進行認可** 如果選取此核取方塊，JavaScript 程式碼編輯器只會在您選擇索引標籤或 Enter 鍵之後，才將語句附加至完成清單中選取的專案。 未選取這個核取方塊時，其他字元像是句號、逗號、冒號、左括號和左大括號 ({) 也可以在陳述式中附加選取的項目。

## <a name="references"></a>參考
 您可以使用這些選項指定不同 JavaScript 專案類型範圍中 IntelliSense .js 檔案的類型。 IntelliSense 參考通常是用來為全域物件提供 IntelliSense 支援。 您也可以使用這個頁面設定必須在執行階段載入之指令碼的載入順序，以及加入 IntelliSense 擴充檔案。

## <a name="uielement-list"></a>UIElement 清單
 **參考群組** 此選項會指定參考群組類型。 支援的參考群組有三種：

 您可以使用預先定義的參考群組指定特殊 IntelliSense .js 檔案於不同 JavaScript 專案範圍中。 有四種參考群組可用：

- 隱含 (Windows *版本*)，適用於使用 JavaScript 的 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] 應用程式。 此群組中所含的檔案會在程式碼編輯器中針對使用 JavaScript 的 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] 應用程式開啟的每個 .js 檔案範圍中。

- 隱含 (Web)，適用於 HTML5 專案。 這個群組中包含的檔案會在程式碼編輯器中針對這些專案類型開啟的每一個 .js 檔案範圍中。

- 專屬的背景工作參考群組，適用於 HTML5 Web 背景工作。 在這個群組中指定的檔案會在具有專屬背景工作參考群組之明確參考的 .js 檔案範圍中。

- 泛型，適用於其他 JavaScript 專案類型。

  **包含** 的檔案此選項會指定將檔案載入至語言服務內容的順序。 您可以使用 [ **移除**]、[ **上移**] 和 [ **下移** ] 按鈕設定順序。 若要讓 IntelliSense 正常運作，相依於另一個檔案的檔案必須在另一個檔案載入後才能載入。

> [!CAUTION]
> 如果以不設條件的方式在兩個以上的隱含參考中定義物件，則這個清單中的最後一個參考將用來定義該物件。

 **新增對群組的參考** 此選項可讓您流覽至適當的檔案，以新增其他的 IntelliSense .js 檔案。

## <a name="see-also"></a>另請參閱
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)
