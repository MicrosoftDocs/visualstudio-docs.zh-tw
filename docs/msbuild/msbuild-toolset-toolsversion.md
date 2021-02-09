---
title: MSBuild 工具組 (ToolsVersion) | Microsoft Docs
description: 瞭解如何在 MSBuild 專案檔中使用 ToolsVersion 屬性，以指定工作、目標和工具的工具組來建立應用程式。
ms.custom: SEO-VS-2020
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b146913365583d49f1d70ebd5ca316f54ca89049
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878223"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild Toolset (ToolsVersion)

MSBuild 使用工作、目標和工具的工具組建置應用程式。 MSBuild 工具組通常會包含一組 *microsoft* 一般的 *.targets* 檔案，以及像是 *csc.exe* 和 *vbc.exe* 的編譯器。 大部分的工具組都可用來將應用程式編譯為多個版本的 .NET Framework 和多個系統平台。 不過，MSBuild 2.0 工具組僅能以 .NET Framework 2.0 為使用目標。

## <a name="toolsversion-attribute"></a>ToolsVersion 屬性

::: moniker range=">=vs-2019"
 在專案檔之 [Project](../msbuild/project-element-msbuild.md) 項目的 `ToolsVersion` 屬性中指定工具組。 下列範例會指定應該使用 MSBuild "Current" 工具組來建置專案。

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 在專案檔之 [Project](../msbuild/project-element-msbuild.md) 項目的 `ToolsVersion` 屬性中指定工具組。 下列範例會指定應該使用 MSBuild 15.0 工具組組建專案。

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> 某些專案類型會使用 `sdk` 屬性，而非 `ToolsVersion` 屬性。 如需詳細資訊，請參閱 [適用于 .Net Core 的 .csproj 格式新增](/dotnet/core/tools/csproj)專案。

## <a name="how-the-toolsversion-attribute-works"></a>ToolsVersion 屬性如何運作

 當您在 Visual Studio 中建立專案，或者升級現有專案時，名為 `ToolsVersion` 的屬性會自動併入專案檔，且其值會對應至 Visual Studio 版本中所包含的 MSBuild 版本。 如需詳細資訊，請參閱 [Framework 目標概觀](../ide/visual-studio-multi-targeting-overview.md)。

 當在專案檔中定義 `ToolsVersion` 值時，MSBuild 會使用該值來判定可用於該專案的工具組屬性值。 一個工具組屬性為 `$(MSBuildToolsPath)`，它會指定 .NET Framework 工具的路徑。 僅需要該工具組屬性 (或 `$(MSBuildBinPath)`)。

 從 Visual Studio 2013 開始，MSBuild 工具組版本就與 Visual Studio 版本號碼相同。 MSBuild 預設為 Visual Studio 中的這個工具組，且位於命令列上，與專案檔中指定的工具組版本無關。  您可以使用 -ToolsVersion 旗標覆寫此行為。 如需詳細資訊，請參閱[覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。

 在下列範例中，MSBuild 會使用 `MSBuildToolsPath` 保留屬性，尋找 *Microsoft.CSharp.targets* 檔案。

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 透過定義自訂工具組，您就可以修改 `MSBuildToolsPath` 的值。 如需詳細資訊，請參閱 [標準和自訂工具](../msbuild/standard-and-custom-toolset-configurations.md)組設定。

 當您在命令列上建置方案並針對 *msbuild.exe* 指定 `ToolsVersion` 時，所有專案及其專案對專案相依性都會根據該 `ToolsVersion` 建置，即使方案中的每個專案都指定其自己的 `ToolsVersion` 也是如此。 若要根據專案來定義 `ToolsVersion` 值，請參閱[覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。

 `ToolsVersion` 屬性也用於專案移轉。 例如，如果您在 Visual Studio 2010 中開啟 Visual Studio 2008 專案，則會上傳專案檔，以包括 ToolsVersion="4.0"。 如果您隨後嘗試在 Visual Studio 2008 中開啟該專案，它不會識別已升級的 `ToolsVersion`，因此會像該屬性仍設為 3.5 那樣建置專案。

 Visual Studio 2010 和 Visual Studio 2012 使用 4.0 的 ToolsVersion。 Visual Studio 2013 使用 12.0 的 ToolsVersion。 Visual Studio 2015 使用 ToolsVersion 14.0，而 Visual Studio 2017 使用 ToolsVersion 15.0。 在許多情況下，專案無需修改，即可在多種版本的 Visual Studio 中開啟。 Visual Studio 一律使用正確的工具組，但是如果所使用的版本與專案檔中的版本不符的話，您會收到通知。 幾乎在所有的情況下，此警告都是良性的，因為工具組在大部分情況下都相容。

 子工具組 (將在本主題稍後說明) 可讓 MSBuild 根據執行建置的內容，自動切換要使用的工具組。 例如，MSBuild 在 Visual Studio 2012 中執行時使用的工具組，比在 Visual Studio 2010 中執行時更新，您不需要明確變更專案檔。

## <a name="toolset-implementation"></a>工具組實作

 選取組成工具組的各種工具、目標和工作的路徑，即可實作工具組。 MSBuild 所定義之工具組中的工具來自下列來源：

- .NET Framework 資料夾。

- 其他 Managed 工具。

  Managed 工具包括 *ResGen.exe* 和 *TlbImp.exe*。

MSBuild 會提供兩種方法來存取工具組：

- 透過使用工具組屬性

- 透過使用 <xref:Microsoft.Build.Utilities.ToolLocationHelper> 方法

工具組屬性會指定工具的路徑。 自 Visual Studio 2017 起，MSBuild 不再具有固定位置。 根據預設，它位於 *MSBuild\15.0\Bin* 資料夾中，相對於 Visual Studio 安裝位置。 在先前的版本中，MSBuild 會使用專案檔中的 `ToolsVersion` 屬性值來尋找對應的登錄機碼，然後使用登錄機碼中的資訊設定工具組屬性。 例如，如果 `ToolsVersion` 有值 `12.0` ，則 MSBuild 會根據以下登錄機碼來設定工具組屬性： **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**。

 以下為工具組屬性：

- `MSBuildToolsPath` 會指定 MSBuild 二進位檔的路徑。

- `SDK40ToolsPath` 會指定 MSBuild 4.x (可能是 4.0 或 4.5) 之其他 Managed 工具的路徑。

- `SDK35ToolsPath` 會指定 MSBuild 3.5 之其他 Managed 工具的路徑。

或者，您可以呼叫 <xref:Microsoft.Build.Utilities.ToolLocationHelper> 類別的方法，即可以程式設計方式判定工具組。 該類別包括下列方法：

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> 會傳回 .NET Framework 資料夾的路徑。

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> 會傳回 .NET Framework 資料夾中檔案的路徑。

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> 會傳回 Managed 工具資料夾的路徑。

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> 會傳回通常位於 Managed 工具資料夾中的檔案路徑。

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) 會傳回建置工具的路徑。

### <a name="sub-toolsets"></a>子工具組

 若為 15.0 之前的 MSBuild 版本，MSBuild 會使用登錄機碼來指定基本工具的路徑。 如果機碼具有子機碼，MSBuild 會使用它指定包含其他工具之子工具組的路徑。 在此情況下，該工具組的定義方式為組合在兩個機碼中定義的屬性定義。

> [!NOTE]
> 如果工具組屬性名稱衝突，為子機碼路徑定義的值會覆寫為根機碼路徑定義的值。

 如果 `VisualStudioVersion` 建置屬性存在，子工具組會變為使用中。 此屬性會採用下列其中一個值：

- "10.0" 會指定 .NET Framework 4 子工具組

- "11.0" 會指定 .NET Framework 4.5 子工具組

- "12.0" 會指定 .NET Framework 4.5.1 子工具組

子工具組 10.0 和 11.0 應該與 ToolsVersion 4.0 搭配使用。 在更新的版本中，子工具組版本應該與 ToolsVersion 相符。

在建置期間，MSBuild 會自動判定並設定 `VisualStudioVersion` 屬性的預設值 (如果尚未定義的話)。

MSBuild 會提供 `ToolLocationHelper` 方法的多載，這些方法可加入 `VisualStudioVersion` 列舉值做為參數

子工具組已引進 .NET Framework 4.5。

## <a name="see-also"></a>另請參閱

- [標準和自訂工具組設定](../msbuild/standard-and-custom-toolset-configurations.md)
- [多目標](../msbuild/msbuild-multitargeting-overview.md)
