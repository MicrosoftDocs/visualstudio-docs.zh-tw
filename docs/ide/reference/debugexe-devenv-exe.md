---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1badcaba6f6461f6a2c6b73580d8d12c50481c2b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948773"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
開啟要偵錯的指定可執行檔。

## <a name="syntax"></a>語法

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>引數
 `ExecutableFile`

 必要。 .exe 檔案的路徑和檔案名稱。

 如果 .exe 檔案找不到或不存在，則不會顯示任何警告或錯誤，而且 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會正常啟動。

## <a name="remarks"></a>備註
 `ExecutableFile` 參數後面的任何字串都會當成引數傳遞給該檔案。

## <a name="example"></a>範例
 下列範例會開啟 `MyApplication.exe` 檔案以進行偵錯。

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)