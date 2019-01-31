---
title: R 程式碼的 IntelliSense
description: 在您鍵入 R 程式碼時，Visual Studio IntelliSense 會顯示有關函式、物件成員、程式碼片段和自動完成的資訊。
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 3ce62d81a3a6fce4e59d43f088d06f0af7385708
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024080"
---
# <a name="intellisense"></a>IntelliSense

在您撰寫程式碼時，Visual Studio IntelliSense 會直接顯示您可以呼叫的函式、物件成員、函式引數和[程式碼片段](code-snippets-for-r.md)等相關資訊。 它也會在您鍵入時顯示可能的完整命令，並在您按 **Tab** 鍵或 **Enter** 鍵時完成 (請參閱 [進階] 索引標籤的 [[編輯器] 選項](editing-r-code-in-visual-studio.md#editor-options))。 在編輯器與 [Interactive 視窗](interactive-repl-for-r-in-visual-studio.md)中皆能使用 IntelliSense。

![顯示函式簽章的 IntelliSense](media/intellisense-function-signature.png)

鍵入函式或其他陳述式時，IntelliSense 會提供自動完成功能表，依您已輸入的內容 (區分大小寫) 來篩選︰

![IntelliSense 自動完成功能表](media/intellisense-auto-complete-menu.png)

按 **Tab** 鍵 (或 **Enter** 鍵、**空格**鍵，視選項的設定方式而定) 插入下拉式清單中選取的項目。 您可以使用方向鍵來變更選取範圍。

IntelliSense 也提供 R 物件成員的建議︰

![物件成員的 IntelliSense 建議](media/intellisense-auto-complete-r-objects.png)

按 **Esc** 鍵時會一併關閉功能表。 您可以用 **Ctrl**+**空格**鍵再次開啟它。

為函式呼叫輸入開頭的 `(` 會插入結尾 `)`，然後叫出簽章說明，如先前所示︰

![函式的 IntelliSense 簽章說明](media/intellisense-function-signature.png)

同樣地，**Esc** 鍵會關閉快顯視窗；針對函式簽章，您可以使用 **Ctrl**+**Shift**+**空格**鍵再次開啟它。

> [!Tip]
> 如果參數說明模糊了下方的文字，請按住 **Ctrl** 鍵讓參數說明文字變成半透明。

## <a name="intellisense-for-user-defined-functions-and-variables"></a>使用者定義函式和變數的 IntelliSense

IntelliSense 適用於相同檔案的使用者定義函式，包括名稱參數完成︰

![使用者定義函式的 IntelliSense](media/intellisense-same-file-functions.png)

![使用者定義函式的 IntelliSense 參數完成](media/intellisense-parameter-completion.png)

IntelliSense 也適用於相同檔案與目前工作階段中的變數︰

![IntelliSense 變數完成](media/intellisense-variable-completion.png)

> [!Note]
> 在 Interactive 視窗中，IntelliSense 只會考量目前 R 工作階段中的名稱，並忽略專案中的檔案。

## <a name="code-suggestions"></a>程式碼建議

當燈泡 (稱為「智慧標籤」) 出現在邊界時，表示 Visual Studio 提醒有常用動作的捷徑可以使用。 例如，將滑鼠停留在編輯器中包含 `library` 陳述式的行，您會看到燈泡。 選取燈泡會顯示可用的選項︰

![編輯器中的 R 智慧標籤](media/intellisense-smart-tags.png)
