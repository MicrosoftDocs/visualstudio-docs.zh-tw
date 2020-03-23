---
title: 符號路徑命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed8ec8e7f990a4a2c5d943a15a105faa5ab23572
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589379"
---
# <a name="symbol-path-command"></a>符號路徑命令
設定目錄清單，以讓偵錯工具搜尋符號。

## <a name="syntax"></a>語法

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>引數
`pathname`

選擇性。 讓偵錯工具搜尋符號的路徑清單 (以分號分隔)。

## <a name="remarks"></a>備註
如果未指定 `pathname`，則此命令會列出目前符號路徑。

## <a name="example"></a>範例
此範例會將兩個路徑新增至符號目錄清單。

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>範例
此範例會顯示以分號分隔的目前符號路徑清單。

```
Debug.SymbolPath
```

## <a name="see-also"></a>另請參閱

- [命令視窗](../../ide/reference/command-window.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
