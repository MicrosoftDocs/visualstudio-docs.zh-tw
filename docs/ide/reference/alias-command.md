---
title: 別名命令
description: 瞭解如何使用 Alias 命令來建立完整命令、完整命令和引數，或另一個別名的新別名。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a20a14cc0f48e86840b770aca934b188bf152dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969785"
---
# <a name="alias-command"></a>別名命令
針對完整命令、完整命令和引數或其他別名，建立新的別名。

> [!TIP]
> 鍵入沒有任何引數的 `>alias` 會顯示目前別名和其定義清單。

## <a name="syntax"></a>語法

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>引數
`aliasname`\
選擇性。 新別名的名稱。 如果未提供 `aliasname` 的值，則會出現目前別名和其定義清單。

`aliasstring`\
選擇性。 完整命令名稱或現有別名，以及任何您想要建立為別名的參數。 如果未提供 `aliasstring` 的值，則會顯示所指定別名的別名和別名字串。

## <a name="switches"></a>交換器
/delete 或 /del 或 /d\
選擇性。 刪除指定的別名，並移除它不進行自動完成。

/reset\
選擇性。 將預先定義的別名清單重設為其原始設定。 亦即，它會還原所有預先定義的別名，並移除所有使用者定義的別名。

## <a name="remarks"></a>備註
因為別名代表命令，所以它們必須位於命令列的開頭。

發出此命令時，您應該在命令後面緊接著參數，而不是別名，否則參數本身將會包含為別名字串的一部分。

`/reset` 參數會在還原別名之前要求確認。 `/reset` 沒有簡短形式。

## <a name="examples"></a>範例
此範例會建立新的別名 `upper`，而這表示完整命令 Edit.MakeUpperCase。

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

此範例會刪除別名 `upper`。

```cmd
>Tools.alias /delete upper
```

此範例會顯示一份所有目前別名和定義的清單。

```cmd
>Tools.Alias
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
