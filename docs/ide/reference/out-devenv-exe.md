---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039456c10993199ec2265042aabc0ed5c475ccd9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954734"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

指定檔案，在您[執行](run-devenv-exe.md)、[執行並結束](runexit-devenv-exe.md)、[升級](upgrade-devenv-exe.md)、[建置](build-devenv-exe.md)、[重建](rebuild-devenv-exe.md)、[清除](clean-devenv-exe.md)或[部署](deploy-devenv-exe.md)方案時儲存及顯示錯誤。

## <a name="syntax"></a>語法

```shell
devenv /Out FileName
```

## <a name="arguments"></a>引數

- *FileName*

  必要項。 當您建置可執行檔時要接收輸出的檔案路徑和名稱。

## <a name="remarks"></a>備註

如果指定不存在的檔案名稱，即會自動建立該檔案。 否則，該檔案已經存在，並將結果附加至檔案的現有內容。

命令列建置錯誤會顯示於 [命令] 視窗以及 [輸出] 視窗的 [方案產生器] 檢視中。 此參數適用於檢視自動組建的結果。

## <a name="example"></a>範例

這個範例會執行 `MySolution` 並將錯誤寫入至檔案 `MyErrorLog.txt`。

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)