---
title: 列出原始碼命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dcecdaa206964e6c8a5aebcadc958fe2c1ee1e5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953187"
---
# <a name="list-source-command"></a>列出原始碼命令
顯示指定的原始程式碼程式行。

## <a name="syntax"></a>語法

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>參數
 /Count:`number`

 選擇性。 指定要顯示的行數。

 /Current

 選擇性。 顯示目前這行。

 /File:`filename`

 選擇性。 要顯示之檔案的路徑。 如果未指定檔名，則此命令會顯示目前陳述式行的原始程式碼。

 /Line:`number`

 選擇性。 顯示特定行號。

 /ShowLineNumbers:`yes|no`

 選擇性。 指定是否顯示行號。

## <a name="example"></a>範例
 此範例列出 Form1.vb 檔案第 4 行的原始程式碼，並顯示行號。

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)