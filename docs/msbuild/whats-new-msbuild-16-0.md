---
title: MSBuild 16.0 的新功能 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 69c576f34b73ec99edd231d39e8bfa8ea661f2ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652803"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 的新功能

此文章說明 MSBuild 16.0 的更新功能和屬性。 有關詳細的版本資訊，請參閱[MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)。

## <a name="changed-path"></a>已變更的路徑

 MSBuild 安裝在 Visual Studio 的每個版本下的 *"當前*"資料夾中，可執行檔位於 *_Bin*子資料夾中。 例如，與 Visual Studio 2019 社區一起安裝的*MSBuild.exe*路徑是*C：*程式檔 （x86）\微軟視覺化工作室\2019_社區\MSBuild_Current_Bin_MSBuild.exe*您還可以使用以下 PowerShell 模組來查找 MSBuild：vssetup.powershell 。 [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)

## <a name="changed-properties"></a>已變更的屬性

 因為新的版本編號，所以已更新下列 MSBuild 屬性。

- 這個工具版本的 `MSBuildToolsVersion` 為 "Current"。 組件版本則與 Visual Studio 2017 的一樣，為 15.1.0.0。

- 這個工具版本的 `VisualStudioVersion` 為 "16.0"。

## <a name="updates"></a>更新

MSBuild (與 Visual Studio) 現在以 .NET Framework 4.7.2 為目標。 若要使用新的 MSBuild API 功能，您的組件也必須升級，但現有的程式碼將繼續運作。

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
