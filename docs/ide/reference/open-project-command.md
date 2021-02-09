---
title: 開啟專案命令
description: 瞭解 [開啟專案] 命令，以及它如何開啟現有的專案或方案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4298c840094f7f1f75e58be1b25213cdf66a6674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881966"
---
# <a name="open-project-command"></a>開啟專案命令

開啟現有的專案或方案。

## <a name="syntax"></a>語法

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>引數

`filename`

必要。 要開啟之專案或方案的完整路徑和檔名。

> [!NOTE]
> `filename` 引數的語法需要包含空格的路徑使用引號。

## <a name="remarks"></a>備註

自動完成會在您鍵入時嘗試找出正確的路徑和檔名。

偵錯時，無法使用此命令。

## <a name="example"></a>範例

下列範例會開啟 Visual Basic 專案 **Test1**：

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
