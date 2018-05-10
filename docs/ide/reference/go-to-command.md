---
title: 移至命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e583ee3bcb764d09bed9907710454dd6c39c6b8d
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="go-to-command"></a>移至命令
將游標移至指定的程式行。

## <a name="syntax"></a>語法

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>引數
 `linenumber`

 選擇性。 整數，代表要移至的行號。

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
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)