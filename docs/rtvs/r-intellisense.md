---
title: R 程式碼的 IntelliSense
description: 在您鍵入 R 程式碼時，Visual Studio IntelliSense 會顯示有關函式、物件成員、程式碼片段和自動完成的資訊。
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 854f7d410e327ca92d0c5156d89bc21765e13cc7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999093"
---
# <a name="intellisense"></a>IntelliSense

在您撰寫程式碼時，Visual Studio IntelliSense 會直接顯示您可以呼叫的函式、物件成員、函式引數和[程式碼片段](code-snippets-for-r.md)等相關資訊。 它還會在鍵入時顯示可能的完成情況，並在按下 **"選項卡"** 或 **"輸入**"鍵時完成（請參閱 **"高級**"選項卡的[編輯器選項](editing-r-code-in-visual-studio.md#editor-options)）。 在編輯器與 [Interactive 視窗](interactive-repl-for-r-in-visual-studio.md)中皆能使用 IntelliSense。

![顯示函式簽章的 IntelliSense](media/intellisense-function-signature.png)

鍵入函式或其他陳述式時，IntelliSense 會提供自動完成功能表，依您已輸入的內容 (區分大小寫) 來篩選︰

![IntelliSense 自動完成功能表](media/intellisense-auto-complete-menu.png)

按 **"選項卡**"（或**輸入**，或**空格**），具體取決於選項的設置方式），插入下拉清單中選定的項。 您可以使用方向鍵來變更選取範圍。

IntelliSense 也提供 R 物件成員的建議︰

![物件成員的 IntelliSense 建議](media/intellisense-auto-complete-r-objects.png)

按**ESC**將完全關閉功能表。 你可以把它帶回來與**Ctrl**+**空間**。

為函式呼叫輸入開頭的 `(` 會插入結尾 `)`，然後叫出簽章說明，如先前所示︰

![函式的 IntelliSense 簽章說明](media/intellisense-function-signature.png)

再次 **，ESC**關閉快顯視窗;對於函數簽名，您可以使用**Ctrl**+**移位**+**空間**再次將其提起。

> [!Tip]
> 如果參數有助於遮蓋其下方的文本，請按住**Ctrl**鍵以使參數有助於文本半透明。

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
