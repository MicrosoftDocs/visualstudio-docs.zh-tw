---
title: 檔案中尋找命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03dc4a1c83b3056e4991da6cecbe6c3b7b97324e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958416"
---
# <a name="find-in-files-command"></a>檔案中尋找命令
在 [尋找和取代] 視窗中，您可以使用 [檔案中尋找] 索引標籤提供的選項子集，搜尋檔案。

## <a name="syntax"></a>語法

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>引數
 `findwhat` 必要項。 要比對的文字。

## <a name="switches"></a>參數
 /case 或 /c 選擇項。 只有當大寫和小寫字元完全符合 `findwhat` 引數中所指定的項目時，才會出現相符項目。

 /ext:`extensions` 選擇項。 指定要搜尋之檔案的副檔名。 如果未指定，就會使用之前輸入的副檔名。

 /lookin:`searchpath` 選擇項。 要搜尋的目錄。 如果路徑包含空格，請將完整路徑用引號括住。

 /names 或 /n 選擇項。 顯示包含相符項目的檔案名稱清單。

 /options 或 /t 選擇項。 顯示目前的尋找選項設定清單，但不會執行搜尋。

 /regex 或 /r 選擇項。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示文字模式，而不是常值字元模式。 如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。

 /reset 或 /e 選擇項。 將尋找選項還原為預設值，但不會執行搜尋。

 /stop 選擇項。 中止目前正在進行中的搜尋作業。 若已指定 `/stop`，則搜尋會忽略所有其他引數。 例如，若要停止目前的搜尋，您會輸入下列項目︰

```cmd
>Edit.FindinFiles /stop
```

 /sub 或 /s 選擇項。 搜尋 /lookin:`searchpath` 引數所指定之目錄內的子資料夾。

 /text2 或 /2 選擇項。 在 [尋找結果 2] 視窗中顯示搜尋結果。

 /wild 或 /l 選擇項。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示字元或字元序列。

 /word 或 /w 選擇項。 僅搜尋全字拼寫。

## <a name="example"></a>範例
 此範例會在 "My Visual Studio Projects" 資料夾的所有 .cls 檔案中搜尋 btnCancel，並在 [尋找結果 2] 視窗中顯示相符項目資訊。

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>請參閱

- [檔案中尋找](../../ide/find-in-files.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)