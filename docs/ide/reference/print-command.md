---
title: 列印命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ef4f0c5c6bd5be2820e1f666529fc43fac59763
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704248"
---
# <a name="print-command"></a>列印命令
評估運算式，或顯示指定的文字。

## <a name="syntax"></a>語法

```cmd
Debug.Print text
```

## <a name="arguments"></a>引數
 `text`

 必要。 要評估的運算式或要顯示的文字。

## <a name="remarks"></a>備註
 您可以使用問號 (?) 作為此命令的別名。 因此；例如，命令

```cmd
>Debug.Print expA
```

 也可以寫成

```cmd
>? expA
```

 此命令的兩個版本都會傳回 `expA` 運算式的目前值。

## <a name="example"></a>範例

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>請參閱

- [評估陳述式命令](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)