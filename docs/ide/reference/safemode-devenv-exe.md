---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f180a45b274ec3042b7e150a43b5e8681fafcfed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593586"
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
