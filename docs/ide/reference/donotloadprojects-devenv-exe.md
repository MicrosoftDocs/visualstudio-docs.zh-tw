---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 03/11/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de757e7022339b11f6d7c04ea7315abf685da24c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428050"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

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

## <a name="see-also"></a>另請參閱

- [Visual Studio 中已篩選的方案](../filtered-solutions.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
