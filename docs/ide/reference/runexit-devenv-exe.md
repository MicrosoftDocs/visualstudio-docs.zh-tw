---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dff2f028c94013df4f69e9aca244f98c307d2782
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948227"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
編譯並執行指定的專案或解決方案，然後關閉整合式開發環境 (IDE)。

## <a name="syntax"></a>語法

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>引數
 `SolutionName`

 必要。 方案檔的完整路徑和名稱。

 `ProjectName`

 必要。 專案檔的完整路徑和名稱。

## <a name="remarks"></a>備註
 根據為使用中方案組態所指定的設定，編譯並執行指定的專案或方案。 這個參數在專案或解決方案執行時會將 IDE 最小化，並在專案或解決方案完成執行之後關閉 IDE。

-   請以雙引號括住包含空格的字串。

-   摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 `/out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例
 這個範例會在最小化的 IDE 中，以使用中部署設定來執行解決方案 `MySolution`，然後關閉 IDE。

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)