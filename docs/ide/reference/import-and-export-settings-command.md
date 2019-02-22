---
title: 匯入和匯出設定命令
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9be5826edf0d7220d30ce5c4a99f333c2ab8b67
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947220"
---
# <a name="import-and-export-settings-command"></a>匯入和匯出設定命令

匯入、匯出或重設 Visual Studio 設定。

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

執行此命令而不使用切換參數，會開啟 [匯入和匯出設定精靈]。 如需詳細資訊，請參閱[同步處理您的設定](../synchronized-settings-in-visual-studio.md)和[環境設定](../environment-settings.md)。

## <a name="example"></a>範例

下列命令會將目前的設定匯出至檔案 `MyFile.vssettings`：

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>另請參閱

- [環境設定](../../ide/environment-settings.md)
- [同步處理您的設定](../../ide/synchronized-settings-in-visual-studio.md)
- [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)