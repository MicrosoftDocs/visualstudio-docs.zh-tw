---
title: 標準和自訂工具組的組態 | Microsoft Docs
description: 深入瞭解標準和自訂的 MSBuild 工具組，其中包含可供您用來建立應用程式專案的工作、目標和工具的參考。
ms.custom: SEO-VS-2020
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70b0d85ea161a3f938013c01702dd2ccce73a31d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956096"
---
# <a name="standard-and-custom-toolset-configurations"></a>標準和自訂工具組的設定

MSBuild 工具組包含工作、目標和工具的參考，可用以組建應用程式專案。 MSBuild 包含標準的工具組，但您也可以建立自訂工具組。 如需如何指定工具組的相關資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>標準工具組設定

::: moniker range=">=vs-2019"
 MSBuild 16.0 包含下列標準工具組：

|ToolsVersion|工具組路徑 (如 MSBuildToolsPath 或 MSBuildBinPath 組建屬性中所指定)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|目前|*\<Visual Studio installation path>\MSBuild\Current\bin*|

 `ToolsVersion` 值決定 Visual Studio 產生的專案使用哪一個工具組。 在 Visual Studio 2019 中，預設值是 "Current" (不論專案檔中指定何種版本)，但您可以在命令提示字元中使用 **/toolsversion** 參數來覆寫該屬性。 如需此屬性的相關資訊以及指定 `ToolsVersion` 的其他方式，請參閱[覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15.0 包含下列標準工具組：

|ToolsVersion|工具組路徑 (如 MSBuildToolsPath 或 MSBuildBinPath 組建屬性中所指定)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Visual Studio installation path>\MSBuild\15.0\bin*|

 `ToolsVersion` 值決定 Visual Studio 產生的專案使用哪一個工具組。 在 Visual Studio 2017 中，預設值是 "15.0" (不論專案檔中指定何種版本)，但您可以在命令提示字元使用 **/toolsversion** 參數覆寫該屬性。 如需此屬性的相關資訊以及指定 `ToolsVersion` 的其他方式，請參閱[覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。
 ::: moniker-end

Visual Studio 2017 及更新版本不會使用登錄機碼作為 MSBuild 的路徑。 若為與 Visual Studio 2017 一同安裝，且為 15.0 版之前的 MSBuild，下列登錄機碼會指定 MSBuild.exe 的安裝路徑。

|登錄機碼|索引鍵名稱|字串索引鍵值|
|------------------|--------------|----------------------|
|**\ HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2。0\\** |**MSBuildToolsPath**|**.NET Framework 2.0 安裝路徑**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**.NET Framework 3.5 安裝路徑**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**.NET Framework 4 安裝路徑**|

### <a name="sub-toolsets"></a>子工具組

 如果前一份表格中的登錄機碼有子機碼，則 MSBuild 會用它來判斷覆寫父工具組中路徑的子工具組路徑。 以下列子機碼為例：

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 如果基底工具組和選取的子工具組中都定義了任何屬性，則系統會使用子工具組中的屬性定義。 例如，MSBuild 4.0 工具組定義 `SDK40ToolsPath` 指向 7.0A SDK，但 MSBuild 4.0\11.0 工具組定義同一屬性指向 8.0A SDK。 如未設定 `VisualStudioVersion`，`SDK40ToolsPath` 會指向 7.0A，但若 `VisualStudioVersion` 設為 11.0，則屬性會改指向 8.0A。

 `VisualStudioVersion` 組建屬性會指出子工具組是否成為作用中。 例如，`VisualStudioVersion` 值為 "12.0" 會指定 MSBuild 12.0 子工具組。 如需詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) 的＜子工具組＞一節。

> [!NOTE]
> 建議您避免變更這些設定。 但您可以新增自己的設定，並定義全電腦的自訂工具組定義，如下節所述。

## <a name="custom-toolset-definitions"></a>自訂工具組定義

 當標準工具組無法滿足您的組建需求時，您可以建立自訂的工具組。 例如，您可能有一個組建實驗室案例，在此案例中，您必須有不同的系統來建立 c + + 專案。 使用自訂工具組，您就可以在建立專案或執行 *MSBuild.exe* 時，將自訂值指派給 `ToolsVersion` 屬性。 透過這樣做，您也可以使用 `$(MSBuildToolsPath)` 屬性匯入該目錄的 *.targets* 檔案，以及定義您自己的自訂工具組屬性，這些屬性可用於使用該工具組的任何專案。

 在 *MSBuild.exe* (如果使用 MSBuild 引擎，則為裝載 MSBuild 引擎的自訂工具) 的設定檔中指定自訂工具組。 例如，如果您想要定義名為 *MyCustomToolset* 的工具組，*MSBuild.exe* 的設定檔可以包含下列工具組定義。

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 也必須在組態檔中定義 `<msbuildToolsets>`，如下所示。

```xml
<configSections>
   <section name="msbuildToolsets"
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,
       Microsoft.Build, Version=15.1.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a"
   </section>
</configSections>
```

> [!NOTE]
> 為正確讀取，`<configSections>` 必須在 `<configuration>` 區段的第一個小節中。

 `ToolsetConfigurationSection` 是可供任何 MSBuild 主機自訂組態使用的自訂組態區段。 如果使用自訂的工具組，主機除提供組態檔項目以外，不必執行任何作業來初始化組建引擎。

 下列屬性專門針對專案中使用的 `ToolsVersion` 值：

- **$(MSBuildBinPath)** 設定為 `ToolsPath` 值，是在登錄或定義 `ToolsVersion` 的組態檔中指定。 登錄或組態檔中的 `$(MSBuildToolsPath)` 設定會指定核心工作和目標的位置。 在專案檔中，這會對應至 $(MSBuildBinPath) 屬性，也會對應至 $(MSBuildToolsPath) 屬性。

- `$(MSBuildToolsPath)` 是保留的屬性，由組態檔中指定的 MSBuildToolsPath 屬性提供。 (這個屬性會取代 `$(MSBuildBinPath)`。 不過， `$(MSBuildBinPath)` 會為了相容性而繼續進行。 ) 自訂工具組必須定義 `$(MSBuildToolsPath)` 或 `$(MSBuildBinPath)` ，但不能同時定義兩者，除非兩者都有相同的值。

  您也可以使用新增 MSBuildToolsPath 屬性時所用的相同語法，在組態檔中新增自訂的工具版本特定屬性。 為使專案檔能夠使用這些自訂屬性，請使用和組態檔指定的值名稱相同的名稱。 您可以在設定檔中定義工具組，但不能定義子工具組。

## <a name="see-also"></a>另請參閱

- [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
