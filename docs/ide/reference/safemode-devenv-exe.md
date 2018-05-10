---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2c678d7304c879cf42c24de9d83704971043676
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
以安全模式啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，並且只載入預設環境和服務。

## <a name="syntax"></a>語法

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>備註
 此參數會在啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時防止載入所有協力廠商 VSPackages，因而確保穩定執行。

## <a name="description"></a>描述
 下列範例會以安全模式啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="code"></a>程式碼

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)