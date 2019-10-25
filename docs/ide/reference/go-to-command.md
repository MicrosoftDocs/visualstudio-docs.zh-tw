---
title: 移至命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5782f5e7dba8d18f9d6f48f345d5e133138e6eea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748742"
---
# <a name="go-to-command"></a>移至命令
將游標移至指定的程式行。

## <a name="syntax"></a>語法

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>引數
`linenumber`\
選擇項。 整數，代表要移至的行號。

## <a name="remarks"></a>備註
行編號是從一開始。 如果 `linenumber` 的值小於一，則會顯示第一行。 如果 `linenumber` 的值大於最後一行的行號，則會顯示最後一行。

如果未指定 `linenumber` 的值，則會顯示 [移至指定行] 對話方塊。

此命令的別名是 GoToLn。

## <a name="example"></a>範例

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)