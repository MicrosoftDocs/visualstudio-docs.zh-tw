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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008802546d87bd44137c6d13ee2aef802877e308
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595874"
---
# <a name="add-existing-project-command"></a>加入現有專案命令
將現有專案新增至目前的方案。

## <a name="syntax"></a>語法

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>引數
`filename`\
選擇性。 要新增至方案的專案完整路徑和專案名稱，包括副檔名。

如果 `filename` 引數包含空格，必須以引號括住。

如果未指定任何檔名，此命令將會開啟 [檔案] 對話方塊，以供使用者選取專案。

## <a name="remarks"></a>備註
自動完成會在您輸入時嘗試找出正確的路徑和檔名。

## <a name="example"></a>範例
此範例會將 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案 TestProject1 新增至目前的方案。

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [視覺化工作室命令別名](../../ide/reference/visual-studio-command-aliases.md)
