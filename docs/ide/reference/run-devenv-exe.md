---
title: -Run (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 051462339ea25dde9c2b55394e1854c60a71dc7e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747766"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

編譯並執行指定的專案或方案。

## <a name="syntax"></a>語法

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>引數

- *SolutionName*

  解決方案檔的完整路徑和名稱。

- *ProjectName*

  專案檔的完整路徑和名稱。

- `/Out` *OutputFilename*

  選擇項。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

根據為使用中解決方案設定指定的設定，編譯並執行指定的專案或解決方案。 此參數會啟動 IDE，並在專案或方案完成執行之後讓它保持作用中。

- 請以雙引號括住包含空格的字串。

- 摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 `/Out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例

此範例會利用使用中部署組態來執行方案 `MySolution`。

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)