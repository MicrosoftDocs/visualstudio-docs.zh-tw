---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b794c80768990a3abac85d3ea3b93699f3b220dd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970431"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

以安全模式啟動 Visual Studio，只載入預設環境和服務。

## <a name="syntax"></a>語法

```shell
devenv /SafeMode
```

## <a name="remarks"></a>備註

此參數會在 Visual Studio 啟動時防止載入所有的協力廠商 VSPackages，因而可確保穩定執行。

## <a name="example"></a>範例

下列範例會以安全模式啟動 Visual Studio。

```shell
devenv /safemode
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)