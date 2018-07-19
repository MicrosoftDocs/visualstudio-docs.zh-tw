---
title: 標準和自訂工具組的組態 | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c38d7ba577beedce8651bb291700a6c071ee7b48
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303012"
---
# <a name="standard-and-custom-toolset-configurations"></a>標準和自訂工具組的組態
MSBuild 工具組包含工作、目標和工具的參考，可用以組建應用程式專案。 MSBuild 包含標準的工具組，但您也可以建立自訂工具組。 如需如何指定工具組的相關資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  
  
## <a name="standard-toolset-configurations"></a>標準工具組組態  
 MSBuild 15.0 包含下列標準工具組：  
  
|ToolsVersion|工具組路徑 (如 MSBuildToolsPath 或 MSBuildBinPath 組建屬性中所指定)|  
|------------------|--------------------------------------------------------------------------------------------|  
|2.0|*Windows 安裝路徑*\Microsoft.Net\Framework\v2.0.50727\|  
|3.5|*Windows 安裝路徑*\Microsoft.NET\Framework\v3.5\|  
|4.0|*Windows 安裝路徑*\Microsoft.NET\Framework\v4.0.30319\|  
|15.0|Visual Studio 安裝路徑\MSBuild\15.0\bin|  
  
 `ToolsVersion` 值決定 Visual Studio 產生的專案使用哪一個工具組。 在 Visual Studio 2017 中，預設值是 "15.0" (不論專案檔中指定何種版本)，但您可以在命令提示字元使用 **/toolsversion** 參數覆寫該屬性。 如需此屬性的相關資訊以及指定 `ToolsVersion` 的其他方式，請參閱[覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。  
  
 Visual Studio 2017 不會使用登錄機碼作為 MSBuild 的路徑。 若為與 Visual Studio 2017 一同安裝，且為 15.0 版之前的 MSBuild，下列登錄機碼會指定 MSBuild.exe 的安裝路徑。  
  
|登錄機碼|索引鍵名稱|字串索引鍵值|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\  |MSBuildToolsPath|.NET Framework 2.0 安裝路徑|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\  |MSBuildToolsPath|.NET Framework 3.5 安裝路徑|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\  |MSBuildToolsPath|.NET Framework 4 安裝路徑|  
  
### <a name="sub-toolsets"></a>子工具組  
 如果前一份資料表中的登錄機碼有子機碼，MSBuild 會將其用以判斷覆寫父工具組中路徑的子工具組路徑。 以下列子機碼為例：  
  
 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  
  
 如果基底工具組和選取的子工具組中定義了任何屬性，則使用子工具組中的屬性定義。 例如，MSBuild 4.0 工具組定義 `SDK40ToolsPath` 指向 7.0A SDK，但 MSBuild 4.0\11.0 工具組定義同一屬性指向 8.0A SDK。 如未設定 `VisualStudioVersion`，`SDK40ToolsPath` 會指向 7.0A，但若 `VisualStudioVersion` 設為 11.0，則屬性會改指向 8.0A。  
  
 `VisualStudioVersion` 組建屬性會指出子工具組是否成為作用中。 例如，`VisualStudioVersion` 值為 "12.0" 會指定 MSBuild 12.0 子工具組。 如需詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) 的＜子工具組＞一節。  
  
> [!NOTE]
>  建議您避免變更這些設定。 但您可以新增自己的設定，並定義全電腦的自訂工具組定義，如下節所述。  
  
## <a name="custom-toolset-definitions"></a>自訂工具組定義  
 當標準工具組無法滿足您的組建需求時，您可以建立自訂的工具組。 例如，您可能有個組建置實驗室案例，必須使用個別的系統組建 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案。 使用自訂工具組，您就可以在建立專案或執行 MSBuild.exe 時，將自訂值指派給 `ToolsVersion` 屬性。 這樣做，也可以使用 `$(MSBuildToolsPath)` 屬性匯入該目錄的 .targets 檔案，以及定義您自己的自訂工具組屬性，這些屬性可用於使用該工具組的任何專案。  
  
 在 MSBuild.exe (如果使用 MSBuild 引擎，則為裝載 MSBuild 引擎的自訂工具) 組態檔中指定自訂的工具組。 例如，如果您想要覆寫 ToolsVersion 15.0 的預設行為，MSBuild.exe 的組態檔可能包含下列工具組定義。  
  
```xml  
<msbuildToolsets default="15.0">  
   <toolset toolsVersion="15.0">  
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
       Microsoft.Build.Engine, Version=15.1.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  為正確讀取，`<configSections>` 必須在 `<configuration>` 區段的第一個小節中。  
  
 `ToolsetConfigurationSection` 是可供任何 MSBuild 主機自訂組態使用的自訂組態區段。 如果使用自訂的工具組，主機除提供組態檔項目以外，不必執行任何作業來初始化組建引擎。 在登錄中定義項目，您就可以指定全電腦的工具組，套用至 MSBuild.exe、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和所有 MSBuild 主機。  
  
> [!NOTE]
>  如果組態檔定義的 `ToolsVersion` 設定已在登錄中定義，這兩個定義不會合併。 組態檔中的定義優先，`ToolsVersion` 的登錄設定則予以忽略。  
  
 下列屬性專門針對專案中使用的 `ToolsVersion` 值：  
  
-   **$(MSBuildBinPath)** 設定為 `ToolsPath` 值，是在登錄或定義 `ToolsVersion` 的組態檔中指定。 登錄或組態檔中的 `$(MSBuildToolsPath)` 設定會指定核心工作和目標的位置。 在專案檔中，這會對應至 $(MSBuildBinPath) 屬性，也會對應至 $(MSBuildToolsPath) 屬性。  
  
-   `$(MSBuildToolsPath)` 是保留的屬性，由組態檔中指定的 MSBuildToolsPath 屬性提供。 (這個屬性會取代 `$(MSBuildBinPath)`。 不過，為相容性之故會執行 `$(MSBuildBinPath)`。)自訂工具組必須定義 `$(MSBuildToolsPath)` 或 `$(MSBuildBinPath)`，但不能同時定義兩者，除非它們有相同的值。  
  
 您也可以使用新增 MSBuildToolsPath 屬性時所用的相同語法，在組態檔中新增自訂的工具版本特定屬性。 為使專案檔能夠使用這些自訂屬性，請使用和組態檔指定的值名稱相同的名稱。 您可以在組態檔中定義工具組，但不能定義子工具組。  
  
## <a name="see-also"></a>請參閱  
 [工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)