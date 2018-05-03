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
ms.openlocfilehash: eaf137b699b7a02a0ee79099e937767262fce4e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
以安全模式啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，並且只載入預設環境和服務。

## <a name="syntax"></a>語法

```
devenv /SafeMode
```

## <a name="remarks"></a>備註
 此參數會在啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時防止載入所有協力廠商 VSPackages，因而確保穩定執行。

## <a name="description"></a>描述
 下列範例會以安全模式啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="code"></a>程式碼

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)