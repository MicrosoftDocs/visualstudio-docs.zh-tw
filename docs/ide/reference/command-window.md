---
title: 命令視窗
description: 瞭解如何使用命令視窗直接在 Visual Studio IDE 中執行命令或別名。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fba1c12743035c397780db64939dec8195a75afd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942850"
---
# <a name="command-window"></a>命令視窗
[命令] 視窗是用來直接在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 中執行命令或別名。 您可以執行功能表命令以及不會出現在任何功能表上的命令。 若要顯示 [命令] 視窗，請從 [檢視] 功能表中選擇 [其他視窗]，然後選取 [命令視窗]。

## <a name="displaying-the-values-of-variables"></a>顯示變數的值
若要檢查 `varA` 變數的值，請使用 [Print 命令](../../ide/reference/print-command.md)：

```cmd
>Debug.Print varA
```

問號 (?) 是 `Debug.Print` 的別名，因此，此命令也可以撰寫為：

```cmd
>? varA
```

此命令的兩個版本都會傳回 `varA` 變數的值。

## <a name="entering-commands"></a>輸入命令
大於符號 (`>`) 會出現在 [命令] 視窗的左邊緣作為新行的提示。 使用向上鍵和向下鍵來捲動先前所發出的命令。

|Task|解決方案|範例|
|----------|--------------|-------------|
|評估運算式。|在運算式前面加上問號 (`?`)。|`? myvar`|
|切換至 [即時運算] 視窗。|將 `immed` 輸入到視窗但沒有大於符號 (>)|`immed`|
|從 [即時運算] 視窗切換回 [命令] 視窗。|將 `cmd` 輸入到視窗。|`>cmd`|

下列快速鍵可協助您在處於命令模式時進行巡覽。

|動作|游標位置|按鍵繫結關係|
|------------| - |----------------|
|循環使用先前輸入的命令清單。|輸入行|向上鍵和向下鍵|
|向上捲動視窗。|命令視窗內容|CTRL+向上鍵|
|向下捲動視窗。|命令視窗內容|向下鍵或 CTRL+向下鍵|

> [!TIP]
> 您可以將整個或一部分的先前命令複製至輸入行，方法是捲動到它，並反白顯示它的全部或一部分，然後按 ENTER。

## <a name="mark-mode"></a>標記模式
當您按一下 [命令] 視窗中的任何先前行時，會自動切換至標記模式。 這可讓您像在任何文字編輯器中一樣地選取、編輯和複製先前命令的文字，並將它們貼入目前行。

## <a name="the-equals--sign"></a>等號 (=)
用來輸入 `EvaluateStatement` 命令的視窗可判斷是否將等號 (=) 解譯為比較運算子或指派運算子。

在 [命令] 視窗中，等號 (=) 會解譯為比較運算子。 您不能在 [命令] 視窗中使用指派運算子。 因此，比方說，如果 `varA` 和 `varB` 變數的值不同，則命令 `>Debug.EvaluateStatement(varA=varB)` 將傳回值 `False`。

相較之下，在 [即時運算] 視窗中，等號 (=) 會解譯為指派運算子。 因此，舉例來說，`>Debug.EvaluateStatement(varA=varB)` 命令會將 `varB` 變數的值指派給變數 `varA`。

## <a name="parameters-switches-and-values"></a>參數、切換參數和值
部分 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令具有必要和選擇性引數、切換參數和值。 處理這類命令時會套用特定規則。 以下是釐清術語的豐富命令範例。

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

在此範例中，

- `Edit.ReplaceInFiles` 是命令

- `/case` 和 `/pattern:regex` 是切換參數 (前面加上斜線 [/] 字元)

- `regex` 是 `/pattern` 切換參數的值；`/case` 切換參數沒有值

- `var[1-3]+` 和 `oldpar` 是參數

    > [!NOTE]
    > 任何包含空格的命令、參數、切換參數或值的兩端都必須有雙引號。

在命令列上，切換參數和參數的位置可以自由地互換，例外是 [Shell](../../ide/reference/shell-command.md) 命令，其切換參數和參數必須為特定順序。

命令所支援的每個切換參數幾乎都會有兩種形式：簡短 (一個字元) 和完整形式。 多個簡短形式的切換參數可以合併成一個群組。 例如，`/p /g /m` 可以改成表示為 `/pgm`。

如果將多個簡短形式的切換參數合併成一個群組，並指定值，則該值會套用至每個切換參數。 例如，`/pgm:123` 等同於 `/p:123 /g:123 /m:123`。 如果群組中的任何切換參數不接受值，就會發生錯誤。

## <a name="escape-characters"></a>逸出字元
命令列中的插入號 (^) 字元表示緊接著的字元會解譯為常值字元，而不是控制字元。 這可用來在參數或參數的值中嵌入一般引號 (")、空格、前置斜線、插入號或任何其他常值字元，但參數名稱除外。 例如，

```cmd
>Edit.Find ^^t /regex
```

無論插入號位於引號內部或外部，功能都相同。 如果插入號是該程式行的最後一個字元，則會將其忽略。 這裡顯示的範例示範如何搜尋模式 "^t"。

## <a name="use-quotes-for-path-names-with-spaces"></a>使用引號括住包含空格的路徑名稱
例如，如果您想要開啟之檔案的路徑包含空格，則必須用雙引號括住包含空格的路徑或路徑區段：**C:\\"Program Files"** 或 **"C:\Program Files"**。

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
