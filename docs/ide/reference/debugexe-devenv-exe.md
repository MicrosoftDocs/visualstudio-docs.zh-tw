---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93a582af62ed0eac8cdc0f5da55ac7bda555152
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008968"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

開啟要偵錯的指定可執行檔。

## <a name="syntax"></a>語法

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>引數

- *ExecutableFile*

  必要項。 `.exe` 檔案的路徑和檔案名稱。 如果 `.exe` 檔案找不到或不存在，則不會顯示任何警告或錯誤，而 Visual Studio 會正常啟動。

## <a name="remarks"></a>備註

*ExecutableFile* 參數後面的任何字串都會當成引數傳遞給該檔案。

## <a name="example"></a>範例

下列範例會開啟 `MyApplication.exe` 檔案以進行偵錯。

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)