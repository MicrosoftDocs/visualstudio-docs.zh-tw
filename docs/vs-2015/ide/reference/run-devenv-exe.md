---
title: -Run (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b2716995e8ff3a318262284b5733a471086c68c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665518"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

編譯並執行指定的專案或方案。

## <a name="syntax"></a>語法

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>引數
 需要 `SolutionName`。 方案檔的完整路徑和名稱。

 需要 `ProjectName`。 專案檔的完整路徑和名稱。

## <a name="remarks"></a>備註
 根據為使用中方案組態所指定的設定，編譯並執行指定的專案或方案。 此參數會啟動整合式開發環境 (IDE)，並在專案或方案完成執行之後讓它保持使用中。

- 請以雙引號括住包含空格的字串。

- 摘要資訊 (包含錯誤) 可以顯示在 [命令]**** 視窗中，或使用 `/out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例
 此範例會利用使用中部署組態來執行方案 `MySolution`。

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>另請參閱
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md) [/Runexit ( # A0) ](../../ide/reference/runexit-devenv-exe.md) [/Build ( # A1) ](../../ide/reference/build-devenv-exe.md) [/Rebuild ( # A2) ](../../ide/reference/rebuild-devenv-exe.md) [/out ( # A3) ](../../ide/reference/out-devenv-exe.md)
