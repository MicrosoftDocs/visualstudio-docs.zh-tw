---
title: 設定目前堆疊框架命令
description: 深入瞭解 [設定目前的堆疊框架] 命令，以及它如何讓您設定特定的堆疊框架。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e1c8d0ade87ee7759593c8a465b43439f71d50d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957747"
---
# <a name="set-current-stack-frame-command"></a>設定目前堆疊框架命令
可讓您設定特定堆疊框架。

## <a name="syntax"></a>語法

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>引數
`index`

必要。 依索引選取堆疊框架。

## <a name="example"></a>範例

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)