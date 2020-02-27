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
ms.openlocfilehash: abd8ba039f9f6a19f5c028e05c03151c090e304c
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630999"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 的新功能

此文章說明 MSBuild 16.0 的更新功能和屬性。 如需詳細的版本資訊，請參閱[MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)。

## <a name="changed-path"></a>已變更的路徑

 MSBuild 安裝於每個 Visual Studio 版本底下的 *\Current* 資料夾中。 例如，*C:\Program Files (x86)\Microsoft Visual Studio\Current\Enterprise\MSBuild*。 您可以使用下列 PowerShell 模組找出 MSBuild：[vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)。

## <a name="changed-properties"></a>已變更的屬性

 因為新的版本編號，所以已更新下列 MSBuild 屬性。

- 這個工具版本的 `MSBuildToolsVersion` 為 "Current"。 組件版本則與 Visual Studio 2017 的一樣，為 15.1.0.0。

- 這個工具版本的 `VisualStudioVersion` 為 "16.0"。

## <a name="updates"></a>更新

MSBuild (與 Visual Studio) 現在以 .NET Framework 4.7.2 為目標。 若要使用新的 MSBuild API 功能，您的組件也必須升級，但現有的程式碼將繼續運作。

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
