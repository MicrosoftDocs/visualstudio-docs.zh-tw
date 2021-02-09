---
title: -DebugExe (devenv.exe)
description: 瞭解如何使用 DebugExe devenv 命令列參數來開啟要進行調試的指定可執行檔。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5cdf770446b78b1a1bb4b55d61f4c3e9f50c4035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894604"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

開啟要偵錯的指定可執行檔。

## <a name="syntax"></a>語法

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>引數

- *ExecutableFile*

  必要。 `.exe` 檔案的路徑和檔案名稱。 如果 `.exe` 檔案找不到或不存在，則不會顯示任何警告或錯誤，而 Visual Studio 會正常啟動。

## <a name="remarks"></a>備註

*ExecutableFile* 參數後面的任何字串都會當成引數傳遞給該檔案。

## <a name="example"></a>範例

下列範例會開啟 `MyApplication.exe` 檔案以進行偵錯。

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
