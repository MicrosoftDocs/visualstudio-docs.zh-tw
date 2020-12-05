---
title: 設定目前處理序
description: 深入瞭解 [設定目前進程] 命令，以及它如何將指定的進程設定為偵錯工具中的使用中進程。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b6a5c2f010b60546fe1ece16f66bf437d2dc633
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616576"
---
# <a name="set-current-process"></a>設定目前處理序
將指定的處理序設為偵錯工具中的使用中處理序。

## <a name="syntax"></a>語法

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>引數
`index`

必要。 處理序的索引。

## <a name="remarks"></a>備註
進行偵錯時，您可以附加至多個處理序，但是無論在任何時間，偵錯工具一次只能有一個使用中處理序。 您可以使用 `SetCurrentProcess` 命令設定使用中處理序。

## <a name="example"></a>範例

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
