---
title: -RunExit (devenv.exe)
description: 瞭解如何使用 RunExit devenv 命令列參數來編譯和執行指定的專案或方案，然後關閉 IDE。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1e0af28e8a96860039381b958d63e161a24936
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039846"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

編譯並執行指定的專案或解決方案，然後關閉整合式開發環境 (IDE)。

## <a name="syntax"></a>語法

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>引數

- *SolutionName*

  方案檔的完整路徑和名稱。

- *ProjectName*

  專案檔的完整路徑和名稱。

- `/Out`*OutputFilename*

  選擇性。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

根據為使用中方案組態所指定的設定，編譯並執行指定的專案或方案。 當專案或方案執行時，此參數會將 IDE 最小化。 它會在專案或方案完成執行之後關閉 IDE。

- 請以雙引號括住包含空格的字串。

- 摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 `/Out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例

這個範例會在最小化的 IDE 中，以使用中部署設定來執行解決方案 `MySolution`，然後關閉 IDE。

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Run ( # A0) ](../../ide/reference/run-devenv-exe.md)
- [/Build ( # A0) ](../../ide/reference/build-devenv-exe.md)
- [/Rebuild ( # A0) ](../../ide/reference/rebuild-devenv-exe.md)
- [/Out ( # A0) ](../../ide/reference/out-devenv-exe.md)
