---
title: MSBuild 15 的現有應用程式更新 | Microsoft Docs
description: 瞭解如何確保應用程式中的程式設計組建符合 Visual Studio 或 MSBuild.exe 內所完成的組建。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd7f47466074536c9088840e726f768f62f9346b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965924"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>MSBuild 15 的現有應用程式更新

在 15.0 之前的 MSBuild 版本，MSBuild 是從全域組件快取 (GAC) 載入，而 MSBuild 延伸模組則已安裝在登錄中。 這可確保所有應用程式都使用相同版本的 MSBuild，且能存取相同的工具組，但導致無法並存安裝不同版本的 Visual Studio。

為了支援更快、更小且並存的安裝，Visual Studio 2017 及更新版本不再將 MSBuild 放置於 GAC 中或修改登錄。 不幸的是，這表示想要使用 MSBuild API 評估或建置專案的應用程式，無法以隱含方式依賴 Visual Studio 安裝。

## <a name="use-msbuild-from-visual-studio"></a>從 Visual Studio 使用 MSBuild

若要確保來自您應用程式的可程式設計建置，符合在 Visual Studio 或 *MSBuild.exe* 內完成的建置，請從 Visual Studio 載入 MSBuild 組件，並使用 Visual Studio 中可用的 SDK。 Microsoft.Build.Locator NuGet 套件可簡化此程序。

## <a name="use-microsoftbuildlocator"></a>使用 Microsoft.Build.Locator

如果您與應用程式一起轉散發 *Microsoft.Build.Locator.dll*，則不需要散發其他 MSBuild 組件。

更新專案以使用 MSBuild 15 和定位器 API，需要在專案中進行一些變更，如下所述。 若要查看更新專案所需的變更範例，請參閱[對 MSBuildLocator 儲存機制中的範例專案所做的認可](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15)。

### <a name="change-msbuild-references"></a>變更 MSBuild 參考

為了確保從中央位置載入 MSBuild，您不得與應用程式一起散發其組件。

變更專案以避免從中央位置載入 MSBuild 的機制，取決於您如何參考 MSBuild。

#### <a name="use-nuget-packages-preferred"></a>使用 NuGet 套件 (慣用)

這些指示假設您使用 [PackageReference 樣式的 NuGet 參考](/nuget/consume-packages/package-references-in-project-files)。

變更您的專案檔案，以從其 NuGet 套件參考 MSBuild 組件。 指定 `ExcludeAssets=runtime` 以告訴 NuGet，只有在建置時需要組件，且不應複製到輸出目錄。

MSBuild 套件的主要和次要版本，必須小於或等於您要支援的 Visual Studio 最小版本。 例如，如果您想要支援 Visual Studio 2017 及更新版本，請參考套件版本 `15.1.548`。

例如，您可以使用這個 XML：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>使用延伸模組組件

如果您無法使用 NuGet 套件，您可以參考與 Visual Studio 一起散發的 MSBuild 組件。 如果您直接參考 MSBuild，請確定它不會透過將 `Copy Local` 設定為 `False` 而複製到您的輸出目錄。 在專案檔中，此設定看起來如下列程式碼：

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>繫結重新導向

參考 Microsoft. 定位器套件，以確保您的應用程式會自動使用必要的系結重新導向至版本15.1.0.0。 此版本的系結重新導向支援 MSBuild 15 和 MSBuild 16。

### <a name="ensure-output-is-clean"></a>確定輸出是乾淨的

建置您的專案，並檢查輸出目錄，以確定其中不含任何非在下一個步驟中新增之 *Microsoft.Build.Locator.dll* 的 *Microsoft.Build.\*.dll* 組件。

### <a name="add-package-reference-for-microsoftbuildlocator"></a>針對 Microsoft.Build.Locator 新增套件參考

針對 [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/) \(英文\) 新增 NuGet 套件參考。

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

請勿針對 Microsoft.Build.Locator 套件指定 `ExcludeAssets=runtime`。

### <a name="register-instance-before-calling-msbuild"></a>註冊執行個體，然後呼叫 MSBuild

> [!IMPORTANT]
> 您無法 `Microsoft.Build` 在呼叫 MSBuildLocator 的方法中，從命名空間) 參考任何 MSBuild 類型 (。 例如，您不能這樣做：
>
> ```csharp
> void ThisWillFail()
> {
>     MSBuildLocator.RegisterDefaults();
>     Project p = new Project(SomePath); // Could be any MSBuild type
>     // Code that uses the MSBuild type
> }
> ```
>
> 相反地，您必須執行下列動作：
>
> ```csharp
> void MethodThatDoesNotDirectlyCallMSBuild()
> {
>     MSBuildLocator.RegisterDefaults();
>     MethodThatCallsMSBuild();
> }
> 
> void MethodThatCallsMSBuild()
> {
>     Project p = new Project(SomePath);
>     // Code that uses the MSBuild type
> }
> ```

新增對定位程式 API 之呼叫最簡單的方式是新增對下列項目的呼叫：

```csharp
MSBuildLocator.RegisterDefaults();
```

您的應用程式啟動程式碼。

如果您想要對 MSBuild 載入進行細部控制，您可以選取 `MSBuildLocator.QueryVisualStudioInstances()` 的結果，以手動方式傳遞給 `MSBuildLocator.RegisterInstance()`，但通常不需要這個動作。
