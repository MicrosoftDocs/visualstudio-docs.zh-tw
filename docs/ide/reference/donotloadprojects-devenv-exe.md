---
title: -DoNotLoadProjects (devenv.exe)
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
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569851"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Visual Studio 2019 版本 16.1 的新功能**

開啟指定的解決方案，而不載入任何專案。 如需詳細資訊，請參閱 [Visual Studio 中已篩選的方案](../filtered-solutions.md)。

## <a name="syntax"></a>語法

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>引數

*解決方案名稱*

必要。 要開啟之解決方案的完整路徑和名稱。

## <a name="example"></a>範例

此範例會開啟方案 MySln.sln，而不載入任何專案。

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 中已篩選的方案](../filtered-solutions.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
