---
title: 檔案中尋找命令
description: 在 [尋找和取代] 視窗的 [檔案中尋找] 索引標籤上，深入瞭解 [尋找] 命令，以及它如何使用一些可用的選項來搜尋檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa0a907332b3ce0164573b809ee9c4b2ac2addda
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305394"
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

`findwhat`\
必要。 要比對的文字。

## <a name="switches"></a>交換器
/case 或 /c\
選擇性。 只有當大寫和小寫字元完全符合 `findwhat` 引數中所指定的項目時，才會出現相符項目。

/ext: `extensions`\
選擇性。 指定要搜尋之檔案的副檔名。 如果未指定，就會使用之前輸入的副檔名。

/lookin: `searchpath`\
選擇性。 要搜尋的目錄。 如果路徑包含空格，請將完整路徑用引號括住。

/names 或 /n\
選擇性。 顯示包含相符項目的檔案名稱清單。

/options 或 /t\
選擇性。 顯示目前的尋找選項設定清單，但不會執行搜尋。

/regex 或 /r\
選擇性。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示文字模式，而不是常值字元模式。 如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。

/reset 或 /e\
選擇性。 將尋找選項還原為預設值，但不會執行搜尋。

/stop\
選擇性。 中止目前正在進行中的搜尋作業。 若已指定 `/stop`，則搜尋會忽略所有其他引數。 例如，若要停止目前的搜尋，您會輸入下列項目︰

```cmd
>Edit.FindinFiles /stop
```

/sub 或 /s\
選擇性。 搜尋 /lookin:`searchpath` 引數所指定之目錄內的子資料夾。

/text2 或 /2\
選擇性。 在 [尋找結果 2] 視窗中顯示搜尋結果。

/wild 或 /l\
選擇性。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示字元或字元序列。

/word 或 /w\
選擇性。 僅搜尋全字拼寫。

## <a name="example"></a>範例
此範例會在 "My Visual Studio Projects" 資料夾的所有 .cls 檔案中搜尋 btnCancel，並在 [尋找結果 2] 視窗中顯示相符項目資訊。

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>另請參閱

- [檔案中尋找](../../ide/find-in-files.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
