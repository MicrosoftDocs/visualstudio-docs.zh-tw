---
description: 匯入、匯出或重設 Visual Studio 設定。 .vssettings 副檔名
title: 匯入和匯出設定命令
ms.date: 05/28/2021
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687635"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>匯入和匯出設定命令 ( .vssettings 檔案) 

匯入、匯出或重設 Visual Studio 設定檔案 `.vssettings` 。

檔案的架構已開啟。 最常見的情況是，架構會遵循 XML 結構，其中每個類別都是標記，它本身就包含子類別標記。 這些子類別標記可以包含屬性值標記。 雖然大部分的封裝都使用通用結構，但是 Visual Studio 中的任何封裝都可以使用它所選擇的架構，對檔案提供任意的 XML。

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>交換器

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
