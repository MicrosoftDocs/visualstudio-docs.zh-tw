---
title: 開啟專案命令
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c1034fbbafa04af2d62526fdbb48812d64e050
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565808"
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

- [視覺化工作室命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [查找/命令框](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
