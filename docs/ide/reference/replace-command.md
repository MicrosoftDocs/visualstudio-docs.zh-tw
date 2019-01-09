---
title: 取代命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b058b57897c369b4f7cc54b849d9abea3a1b6b15
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989227"
---
# <a name="replace-command"></a>取代命令
使用在 [尋找和取代] 視窗 [檔案中取代] 索引標籤提供的選項子集，取代檔案中的文字。

## <a name="syntax"></a>語法

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>引數
 `findwhat`

 必要項。 要比對的文字。

 `replacewith`

 必要項。 要用來取代相符文字的文字。

## <a name="switches"></a>參數
 /all 或 /a

 選擇性。 以取代文字來取代所有出現的搜尋文字。

 /case 或 /c

 選擇性。 只有當大寫和小寫字元完全符合 `findwhat` 引數中所指定的項目時，才會出現相符項目。

 /doc 或 /d

 選擇性。 僅搜尋目前的文件。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /hidden 或 /h

 選擇性。 搜尋隱藏和摺疊的文字，例如設計階段控制項的中繼資料、大綱文字的隱藏區域，或是摺疊的類別或方法。

 /open 或 /o

 選擇性。 將所有開啟的文件當成一份文件搜尋。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /options 或 /t

 選擇性。 顯示目前的尋找選項設定清單，但不會執行搜尋。

 /proc 或 /p

 選擇性。 只搜尋目前的程序。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /regex 或 /r

 選擇性。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示文字模式，而不是常值字元模式。 如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。

 /reset 或 /e

 選擇性。 將尋找選項還原為預設值，但不會執行搜尋。

 /sel 或 /s

 選擇性。 只搜尋目前的選取範圍。 只指定其中一個可用的搜尋範圍，`/doc`、`/proc`、`/open` 或 `/sel`。

 /up 或 /u

 選擇性。 從檔案目前的位置向檔案頂端進行搜尋。 預設從檔案目前的位置開始向檔案底部進行搜尋。

 /wild 或 /l

 選擇性。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示字元或字元序列。

 /word 或 /w

 選擇性。 僅搜尋全字拼寫。

## <a name="example"></a>範例
 此範例會將在所有開啟的文件中的 `btnSend` 取代為 `btnSubmit`。

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>請參閱

- [尋找和取代文字](../../ide/finding-and-replacing-text.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)