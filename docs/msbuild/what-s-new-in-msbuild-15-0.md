---
title: "MSBuild 15 中的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
caps.latest.revision: "23"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e31746567a300ea8f9a62079ab1392fe9f1e0ec8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15 的新功能
MSBuild 現在已可當作 [.NET Core SDK](https://www.microsoft.com/net/download/core) 的一部分來取得，並且可以在 Windows、macOS 和 Linux 上建置 .NET Core 專案。  

## <a name="changed-path"></a>已變更的路徑
 MSBuild 現已安裝在每個 Visual Studio 版本底下的資料夾中。 例如，`C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`。 您可以使用下列 PowerShell 模組找出 MSBuild：[vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)。

 MSBuild 已不再安裝於「全域組件快取」。 若要以程式設計的方式參考 MSBuild，請使用 NuGet 套件。

## <a name="changed-properties"></a>已變更的屬性  
 因為新的版本編號，所以已更新下列 MSBuild 屬性。  

-   該工具此版本的 `MSBuildToolsVersion` 是 15.0。 組件版本是 15.1.0.0。

-   `MSBuildToolsPath` 不再有固定位置。 根據預設，它是位在相對於 Visual Studio 安裝位置的 MSBuild\15.0\Bin 資料夾，但是 Visual Studio 的安裝位置可在安裝時變更。

-   `ToolsVersion` 值不會再設定於登錄中。  

-   `SDK35ToolsPath` 和 `SDK40ToolsPath` 屬性指向與此版本 Visual Studio 一起封裝的 .NET Framework SDK (例如 4.X 工具的 10.0A)。  

## <a name="updates"></a>更新
- [Project 元素](../msbuild/project-element-msbuild.md)有新的 `SDK` 屬性。 而 `Xmlns` 屬性現在是選擇性的。
- 目標外的 [Item 元素](../msbuild/item-element-msbuild.md)有新的 `Update` 屬性。 此外，已經移除對 `Remove` 屬性的限制。
- `Directory.Build.props` 是使用者定義的檔案，可讓您自訂目錄下的專案。 除非屬性 `ImportDirectoryBuildTargets` 設為 **false**，否則系統會從 Microsoft.Common.props 自動匯入這個檔案。 `Directory.Build.targets` 是由 Microsoft.Common.targets 匯入。
- 任何未與目前屬性清單衝突的中繼資料，您即可選擇將其表示為屬性。 如需詳細資訊，請參閱 [Item 元素](../msbuild/item-element-msbuild.md)。

## <a name="new-property-functions"></a>新的屬性函式

- 如果路徑沒有結尾斜線，`EnsureTrailingSlash` 會加上斜線。
- `NormalizePath` 會結合路徑元素，並確保輸出字串具有適用於目前作業系統的正確目錄分隔字元。
- `NormalizeDirectory` 會結合路徑元素，確保具有結尾斜線，及確保輸出字串具有適用於目前作業系統的正確目錄分隔字元。
- `GetPathOfFileAbove` 會傳回此檔案前一個檔案的路徑。 它在功能上相當於呼叫 `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>另請參閱
[ MSBuild](../msbuild/msbuild.md)
