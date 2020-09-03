---
title: 設定基數命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665412"
---
# <a name="set-radix-command"></a>設定基數命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

設定或傳回用來顯示整數值的數值基底。

## <a name="syntax"></a>語法

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>引數
 `10` 或或或 `16` `hex` `dec` 選擇性。 表示十進位 (10 或 dec) 或十六進位 (16 或 hex)。 如果省略引數，則會傳回目前基數值。

## <a name="example"></a>範例
 此範例設定環境以十六進位格式顯示整數值。

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>另請參閱
 [Visual Studio](../../ide/reference/visual-studio-commands.md)命令[視窗](../../ide/reference/command-window.md)[尋找/命令箱](../../ide/find-command-box.md) [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
