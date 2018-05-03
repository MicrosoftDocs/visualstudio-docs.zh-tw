---
title: devenv.exe setup 參數
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

/Setup 參數會讓 Visual Studio 合併所有來自可用 VSPackages 的資源中繼資料 (其描述功能表、工具列和命令群組)。

## <a name="syntax"></a>語法

```shell
devenv /setup
```

## <a name="remarks"></a>備註

此參數不需使用引數。 一般來說，會將 `devenv /setup` 命令指定為安裝程序的最後一個步驟。 使用 `/setup` 參數不會啟動 Visual Studio。

> [!NOTE]
> 您必須以系統管理員身分執行 `devenv`，才能使用 `/setup` 參數。

## <a name="example"></a>範例

這個範例會示範含 VSPackages 之 Visual Studio 版本的最後一個安裝步驟 。

```shell
devenv /setup
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)