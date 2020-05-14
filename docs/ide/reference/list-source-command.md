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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c211773f20ab4643b62c8c71fc6ae6581a91987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747895"
---
# <a name="list-source-command"></a>列出原始碼命令
顯示指定的原始程式碼程式行。

## <a name="syntax"></a>語法

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>交換器
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

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)