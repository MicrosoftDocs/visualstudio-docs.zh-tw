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
ms.openlocfilehash: 7cf241ec0a9ff849b52761a241e84a15d287bb88
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="print-command"></a>列印命令
評估運算式，或顯示指定的文字。

## <a name="syntax"></a>語法

```
Debug.Print text
```

## <a name="arguments"></a>引數
 `text`

 必要。 要評估的運算式或要顯示的文字。

## <a name="remarks"></a>備註
 您可以使用問號 (?) 作為此命令的別名。 因此；例如，命令

```
>Debug.Print expA
```

 也可以寫成

```
>? expA
```

 此命令的兩個版本都會傳回 `expA` 運算式的目前值。

## <a name="example"></a>範例

```
>Debug.Print varA
```

## <a name="see-also"></a>請參閱

- [評估陳述式命令](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)