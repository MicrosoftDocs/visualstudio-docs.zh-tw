---
title: -UseEnv (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b597eae42eb36c8d034ca9a4038b6823c1121349
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846330"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

啟動 Visual Studio 並將環境變數載入 [VC++ 目錄] 對話方塊中。

> [!NOTE]
> 此參數的安裝包含 **使用 C++ 的桌面開發**工作負載。

## <a name="syntax"></a>語法

```shell
Devenv /useenv
```

## <a name="example"></a>範例

下列範例會啟動 Visual Studio 並將環境變數載入 [VC++ 目錄] 對話方塊中。

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>另請參閱

* [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)