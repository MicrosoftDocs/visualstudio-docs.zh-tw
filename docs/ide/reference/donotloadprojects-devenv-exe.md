---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34fe7dfed2774eace7d32b1c9041355b566d4e76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654499"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Visual Studio 2019 版本 16.1 的新功能**

開啟指定的解決方案，而不載入任何專案。 如需詳細資訊，請參閱 [Visual Studio 中已篩選的方案](../filtered-solutions.md)。

## <a name="syntax"></a>語法

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>引數

*SolutionName*

必要項。 要開啟之解決方案的完整路徑和名稱。

## <a name="example"></a>範例

此範例會開啟方案 MySln.sln，而不載入任何專案。

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>請參閱

- [Visual Studio 中已篩選的方案](../filtered-solutions.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
