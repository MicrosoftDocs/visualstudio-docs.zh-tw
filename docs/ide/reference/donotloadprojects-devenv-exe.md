---
title: -DoNotLoadProjects (devenv.exe)
description: 瞭解如何使用 DoNotLoadProjects devenv 命令列參數來開啟指定的方案，而不需要載入任何專案。
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040624"
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

必要。 要開啟之解決方案的完整路徑和名稱。

## <a name="example"></a>範例

此範例會開啟方案 MySln.sln，而不載入任何專案。

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 中已篩選的方案](../filtered-solutions.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
