---
title: 加入現有專案命令
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0946efb15758c76c078ff234717af6fd1fac15c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951627"
---
# <a name="add-existing-project-command"></a>加入現有專案命令
將現有專案新增至目前的方案。

## <a name="syntax"></a>語法

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>引數
 `filename` 選擇項。 要新增至方案的專案完整路徑和專案名稱，包括副檔名。

 如果 `filename` 引數包含空格，必須以引號括住。

 如果未指定任何檔名，此命令將會開啟 [檔案] 對話方塊，以供使用者選取專案。

## <a name="remarks"></a>備註
 自動完成會在您輸入時嘗試找出正確的路徑和檔名。

## <a name="example"></a>範例
 此範例會將 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案 TestProject1 新增至目前的方案。

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)