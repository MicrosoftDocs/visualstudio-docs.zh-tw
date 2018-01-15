---
title: "devenv.exe 安裝參數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f03de74540d130d66ce123b355691e0828b93e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

/Setup 參數會讓 Visual Studio 合併所有來自可用 VSPackages 的資源中繼資料 (其描述功能表、工具列和命令群組)。

## <a name="syntax"></a>語法

```
devenv /setup
```

## <a name="remarks"></a>備註

此參數不需使用引數。 一般來說，會將 `devenv /setup` 命令指定為安裝程序的最後一個步驟。 使用 `/setup` 參數不會啟動 Visual Studio。

您必須以系統管理員身分執行 `devenv` ，才能使用 [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) 和 [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) 參數。

## <a name="example"></a>範例

這個範例會示範含 VSPackages 之 Visual Studio 版本的最後一個安裝步驟 。

```
devenv /setup
```

## <a name="see-also"></a>另請參閱

[Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)