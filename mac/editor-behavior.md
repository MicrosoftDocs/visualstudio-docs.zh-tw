---
title: 程式碼格式設定
description: 本文說明可用來修改 Visual Studio for Mac 中文字編輯器行為的各種選項
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 20363d5497ea5897cb2685ca838da44b8c21d3df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823179"
---
# <a name="editor-behavior"></a>編輯器的行為

可以設定編輯器的行為，讓程式碼在撰寫時即格式化。 這些動作是在 [ **文字編輯器] Visual Studio > > 喜好**設定下設定 > 行為，而一些較常用的函式則如下所述：

![編輯器的行為選項](media/source-editor-image9.png)

* 建立新的類別、方法或屬性時，對稱的右大括弧可以自動新增到程式碼。 選取此選項時，輸入 `{` 會自動新增 `}`。
* 字元按壓會觸發即時程式碼格式化，例如分號或大括弧，這會模擬設定的格式化喜好設定。
* 您也可以選擇在儲存檔案時將它格式化，如此可以視需要撰寫程式碼，讓 IDE 負責依現有喜好設定所設定地進行程式碼格式化。
* 縮排可設定為無、自動或智慧型。 這些會執行下列動作：
  * 無 - 將插入號設定到下一行的開頭
  * 自動 - 將插入號設定到下一行的相同資料行
  * 智慧型 - 根據程式碼在下一行進行縮排
* 各個作業系統之間的斷詞行為不同，而為了瀏覽目的，文字編輯器必須知道單字開頭或結尾的位置。 格式化可以設定為 Unix 或 Windows。

您也可以設定 XML、CSS、HTML 和 JSON 的格式化規則。

## <a name="see-also"></a>另請參閱

- [程式碼樣式喜好設定 (Windows 上的 Visual Studio)](/visualstudio/ide/code-styles-and-quick-actions)
