---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6199bf96bc631cf1018b2cb72a4d3c3cf7c703cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
清除所有選項，以略過載入使用者新增的 VSPackage，避免載入有問題的 VSPackage，然後啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="syntax"></a>語法

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>備註
 SkipLoading 標記的存在會停用 VSPackage 的載入，清除標記則會重新啟用載入 VSPackage。

## <a name="example"></a>範例
 下列範例會清除所有的 SkipLoading 標記。

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)