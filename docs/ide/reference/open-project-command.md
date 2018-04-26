---
title: 開啟專案命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09241e72119a0a0973995b16152941bbe5272c3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="open-project-command"></a>開啟專案命令
開啟現有專案。

## <a name="syntax"></a>語法

```
File.OpenProject filename
```

## <a name="arguments"></a>引數
 `filename`

 必要。 要開啟之專案的完整路徑和檔案名稱。

 `filename` 引數的語法需要包含空格的路徑使用引號。

## <a name="remarks"></a>備註
 自動完成會在您輸入時嘗試找出正確的路徑和檔名。

 偵錯時，無法使用此命令。

## <a name="example"></a>範例
 此範例會開啟 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案 Test1。

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)