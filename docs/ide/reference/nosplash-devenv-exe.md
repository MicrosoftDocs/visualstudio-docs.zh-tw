---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794934ab0bddcc90a36accf639b26e5ecc6bab30
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54233140"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

防止顯示啟動顯示畫面。

## <a name="syntax"></a>語法

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>引數

- *File1*

  選擇性。 要在現有 Visual Studio 執行個體中開啟的檔案。 如果沒有任何 Visual Studio 執行個體存在，即會建立具有簡易視窗配置的新執行個體，而工具會在新的執行個體中開啟 *File1*。

- *FileN*

  選擇性。 要在現有 Visual Studio 執行個體中開啟的一或多個其他檔案。

## <a name="remarks"></a>備註

此參數會隱藏啟動顯示畫面。 忽略這個參數會導致啟動顯示畫面顯示。 如果您想要進一步檢查啟動顯示畫面 (例如，檢查 VSPackage 產品圖示)，請使用 [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) 參數。

`/NoSplash` 參數可以與其他參數相結合，例如 [/Run](run-devenv-exe.md) 或 [/DebugExe](debugexe-devenv-exe.md)。

## <a name="example"></a>範例

這三個範例全都會開啟 IDE，而不會顯示啟動顯示畫面。 第二個範例也會編譯指定的方案，並執行建置的可執行檔。 第三個範例會開啟指定的可執行檔，以便在 IDE 中進行偵錯。

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [適用於 VSPackage 開發的 Devenv 命令列參數](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
