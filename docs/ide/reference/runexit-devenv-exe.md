---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 295d4999437248cc9221631378c2beffd80094d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655527"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

編譯並執行指定的專案或解決方案，然後關閉整合式開發環境 (IDE)。

## <a name="syntax"></a>語法

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>引數

- *SolutionName*

  解決方案檔的完整路徑和名稱。

- *ProjectName*

  專案檔的完整路徑和名稱。

- `/Out` *OutputFilename*

  選擇項。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

根據為使用中解決方案設定指定的設定，編譯並執行指定的專案或解決方案。 當專案或方案執行時，此參數會將 IDE 最小化。 它會在專案或方案完成執行之後關閉 IDE。

- 請以雙引號括住包含空格的字串。

- 摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 `/Out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例

這個範例會在最小化的 IDE 中，以使用中部署設定來執行解決方案 `MySolution`，然後關閉 IDE。

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)