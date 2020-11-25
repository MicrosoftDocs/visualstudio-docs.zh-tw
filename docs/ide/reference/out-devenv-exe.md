---
title: -Out (devenv.exe)
description: 瞭解如何使用 Out devenv 命令列參數來指定要儲存的檔案，並在執行、執行和結束、升級、建立、重建、清理或部署解決方案時顯示錯誤。
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06409d3b7e3d218fcf2b81dce7ea58d3202b7e21
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040052"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

指定檔案，在您[執行](run-devenv-exe.md)、[執行並結束](runexit-devenv-exe.md)、[升級](upgrade-devenv-exe.md)、[建置](build-devenv-exe.md)、[重建](rebuild-devenv-exe.md)、[清除](clean-devenv-exe.md)或[部署](deploy-devenv-exe.md)方案時儲存及顯示錯誤。

## <a name="syntax"></a>語法

```shell
devenv /Out FileName
```

## <a name="arguments"></a>引數

- *FileName*

  必要。 當您建置可執行檔時要接收輸出的檔案路徑和名稱。

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
- [/Run ( # A0) ](../../ide/reference/run-devenv-exe.md)
- [/RunExit ( # A0) ](runexit-devenv-exe.md)
- [/Upgrade ( # A0) ](upgrade-devenv-exe.md)
- [/Clean ( # A0) ](clean-devenv-exe.md)
- [/Build ( # A0) ](../../ide/reference/build-devenv-exe.md)
- [/Rebuild ( # A0) ](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy ( # A0) ](../../ide/reference/deploy-devenv-exe.md)
