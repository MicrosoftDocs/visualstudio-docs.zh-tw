---
title: 設定目前執行緒命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ea652f04295871f9437d80555254caecab87a48
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926058"
---
# <a name="set-current-thread-command"></a>設定目前執行緒命令
將指定的執行緒設為目前執行緒。

## <a name="syntax"></a>語法

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>引數
`index`

必要項。 依索引選取執行緒。

## <a name="example"></a>範例

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)