---
title: 設定目前執行緒命令
description: 瞭解「設定目前線程」命令，以及它如何將指定的執行緒設定為目前的執行緒。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2cb58bf8751eb4299ecede18bac83770c3a7df96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957734"
---
# <a name="set-current-thread-command"></a>設定目前執行緒命令
將指定的執行緒設為目前執行緒。

## <a name="syntax"></a>語法

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>引數
`index`

必要。 依索引選取執行緒。

## <a name="example"></a>範例

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)