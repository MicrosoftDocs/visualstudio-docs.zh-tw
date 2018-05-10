---
title: 開啟方案命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 576146e8bcbc20babff10f2a55d561f532a80723
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="open-solution-command"></a>開啟方案命令
關閉任何其他開啟的方案，以開啟現有方案。

## <a name="syntax"></a>語法

```cmd
File.OpenSolution filename
```

## <a name="arguments"></a>引數
 `Filename`

 必要。 要開啟之方案的完整路徑和檔名。

 `filename` 引數的語法需要包含空格的路徑使用引號。

## <a name="remarks"></a>備註
 自動完成會在您輸入時嘗試找出正確的路徑和檔名。

## <a name="example"></a>範例
 此範例會開啟 Test1.sln 方案。

```cmd
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)