---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
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
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945475"
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