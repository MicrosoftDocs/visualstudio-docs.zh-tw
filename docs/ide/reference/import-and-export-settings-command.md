---
title: 匯入和匯出設定命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4119abf74281e3c0dbb2b3d5f3ef472a0527a08f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704583"
---
# <a name="import-and-export-settings-command"></a>匯入和匯出設定命令
匯入、匯出或重設 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 設定。

## <a name="syntax"></a>語法

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>參數
 /export:`filename`

 選擇性。 將目前的設定匯出至指定的檔案。

 /import:`filename`

 選擇性。 匯入指定檔案中的設定。

 /reset

 選擇性。 重設目前的設定。

## <a name="remarks"></a>備註

執行此命令而不使用切換參數，會開啟 [匯入和匯出設定精靈]。 如需詳細資訊，請參閱[同步處理您的設定](../../ide/synchronized-settings-in-visual-studio.md)。

## <a name="example"></a>範例

下列命令會將目前的設定匯出至檔案 `MyFile.vssettings`。

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>另請參閱

- [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)