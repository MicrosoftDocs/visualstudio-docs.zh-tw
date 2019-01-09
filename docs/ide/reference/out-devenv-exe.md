---
title: -Out (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f240b464ddba4e0549e3faff432685201e4560f6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985637"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
指定檔案以在您執行、建置、重建或部署解決方案時儲存及顯示錯誤。

## <a name="syntax"></a>語法

```cmd
devenv /out FileName
```

## <a name="arguments"></a>引數
 `FileName`

 必要項。 當您建置可執行檔時要接收錯誤的檔案路徑和名稱。

## <a name="remarks"></a>備註
 如果指定不存在的檔名，會自動建立該檔案。 如果檔案已經存在，則結果會附加至檔案的現有內容。

 命令列建置錯誤顯示在 [命令] 視窗與 [輸出] 視窗的 [解決方案產生器] 檢視。 如果您正在執行自動建置，而且需要查看結果，這個選項非常有用。

## <a name="example"></a>範例
 這個範例會執行 `MySolution` 並將錯誤寫入至檔案 `MyErrorLog.txt`。

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)