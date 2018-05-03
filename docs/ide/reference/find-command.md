---
title: 尋找命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31810189ec7127548f68a3732afc701e8a7bac08
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="find-command"></a>尋找命令
在 [尋找和取代] 視窗中，您可以使用 [檔案中尋找] 索引標籤提供的選項子集，搜尋檔案。

## <a name="syntax"></a>語法

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>引數
 `findwhat` 必要。 要比對的文字。

## <a name="switches"></a>參數
 /case 或 /c 選擇項。 只有當大寫和小寫字元完全符合 `findwhat` 引數中所指定的項目時，才會出現相符項目。

 /doc 或 /d 選擇項。 僅搜尋目前的文件。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /markall 或 /m 選擇項。 將圖形放在每一行，每行包含一個目前文件內的搜尋相符項目。

 /open 或 /o 選擇項。 將所有開啟的文件當成一份文件搜尋。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /options 或 /t 選擇項。 顯示目前的尋找選項設定清單，但不會執行搜尋。

 /proc 或 /p 選擇項。 只搜尋目前的程序。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /reset 或 /e 選擇項。 將尋找選項還原為預設值，但不會執行搜尋。

 /sel 或 /s 選擇項。 只搜尋目前的選取範圍。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /up 或 /u 選擇項。 從檔案目前的位置向檔案開頭處進行搜尋。 預設從檔案目前的位置開始向檔案結尾處進行搜尋。

 /regex 或 /r 選擇項。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示文字模式，而不是常值字元模式。 如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。

 /wild 或 /l 選擇項。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示字元或字元序列。

 /word 或 /w 選擇項。 僅搜尋全字拼寫。

## <a name="example"></a>範例
 此範例會在目前選取的程式碼區段中，對 "somestring" 執行區分大小寫的搜尋。

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>請參閱

- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)