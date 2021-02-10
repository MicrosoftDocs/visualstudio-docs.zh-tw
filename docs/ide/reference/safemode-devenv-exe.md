---
title: -SafeMode (devenv.exe)
description: 瞭解如何使用安全模式 devenv 命令列參數，以安全模式啟動 Visual Studio，只載入預設環境和服務。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957864"
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
