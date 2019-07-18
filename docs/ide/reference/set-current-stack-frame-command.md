---
title: 設定目前堆疊框架命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eea69dc4d2931f66d4c6769667e23bdfb4eecf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934521"
---
# <a name="set-current-stack-frame-command"></a>設定目前堆疊框架命令
可讓您設定特定堆疊框架。

## <a name="syntax"></a>語法

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>引數
 `index`

 必要項。 依索引選取堆疊框架。

## <a name="example"></a>範例

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)