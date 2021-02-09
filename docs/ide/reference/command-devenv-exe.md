---
title: -Command (devenv.exe)
description: 瞭解如何在啟動 Visual Studio IDE 之後，使用命令 devenv 命令列參數來執行指定的命令。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38738dad275b38fe0c5a6a70104e80f6a794bab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882182"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

在啟動 Visual Studio IDE 之後，執行指定的命令。

## <a name="syntax"></a>語法

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>引數

*CommandName*

必要。 Visual Studio 命令的完整名稱或其別名，以雙引號括住。 如需命令和別名語法的詳細資訊，請參閱 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)。

## <a name="remarks"></a>備註

啟動完成後，IDE 會執行具名命令。

::: moniker range="vs-2017"

如果您使用此參數，IDE 在啟動時就不會顯示 [起始頁]。

::: moniker-end

如果增益集公開某個命令，則可從命令列中使用此參數啟動增益集。 如需詳細資訊，請參閱 [如何：使用增益集管理員來控制增益集](/previous-versions/xwdatdwh(v=vs.140))。

## <a name="example"></a>範例

此範例會啟動 Visual Studio，並自動執行巨集 Open Favorite Files。

第二個範例會在 IDE 中開啟網頁瀏覽索引標籤，並瀏覽到 Microsoft Docs 網站。

第三個範例會建立稱為 `some_file.cs` 的新檔案，並在程式碼編輯器中開啟它。

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
- [命令視窗](command-window.md)
