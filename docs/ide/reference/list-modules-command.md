---
title: 列出模組命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54e975cf886f0bb8392bd3679a28bae6bb6bfe00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944657"
---
# <a name="list-modules-command"></a>列出模組命令
列出目前處理序的模組。

## <a name="syntax"></a>語法

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>參數
 /Address:`yes|no`

 選擇性。 指定是否要顯示模組的記憶體位址。 預設值為 `yes`。

 /Name:`yes|no`

 選擇性。 指定是否要顯示模組的名稱。 預設值為 `yes`。

 /Order:`yes|no`

 選擇性。 指定是否要顯示模組的順序。 預設值為 `no`。

 /Path:`yes|no`

 選擇性。 指定是否要顯示模組的路徑。 預設值為 `yes`。

 /Process:`yes|no`

 選擇性。 指定是否要顯示模組的處理序。 預設值為 `no`。

 /SymbolFile:`yes|no`

 選擇性。 指定是否要顯示模組的符號檔。 預設值為 `no`。

 /SymbolStatus:`yes|no`

 選擇性。 指定是否要顯示模組的符號狀態。 預設值為 `yes`。

 /Timestamp:`yes|no`

 選擇性。 指定是否要顯示模組的時間戳記。 預設值為 `no`。

 /Version:`yes|no`

 選擇性。 指定是否要顯示模組的版本。 預設值為 `no`。

## <a name="example"></a>範例
 這個範例會列出模組名稱、位址，以及目前處理序的時間戳記。

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [如何：使用模組視窗](../../debugger/how-to-use-the-modules-window.md)