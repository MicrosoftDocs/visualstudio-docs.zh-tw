# <a name="updating-an-existing-application-for-msbuild-15"></a>MSBuild 15 的現有應用程式更新

在 15.0 之前的 MSBuild 版本，MSBuild 是從全域組件快取 (GAC) 載入，而 MSBuild 延伸模組則已安裝在登錄中。 這可確保所有應用程式都使用相同版本的 MSBuild，且能存取相同的工具組，但導致無法並存安裝不同版本的 Visual Studio。

為了支援更快、更小且並存的安裝，Visual Studio 2017 不再將 MSBuild 放在 GAC 中或修改登錄。 不幸的是，這表示想要使用 MSBuild API 評估或建置專案的應用程式，無法以隱含方式依賴 Visual Studio 安裝。

## <a name="using-msbuild-from-visual-studio"></a>從 Visual Studio 使用 MSBuild

若要確保來自您應用程式的可程式設計建置，符合在 Visual Studio 或 MSBuild.exe 內完成的建置，請從 Visual Studio 載入 MSBuild 組件，並使用 Visual Studio 中可用的 SDK。 Microsoft.Build.Locator NuGet 套件可簡化此作業。

## <a name="using-microsoftbuildlocator"></a>使用 Microsoft.Build.Locator

如果您與應用程式一起轉散發 `Microsoft.Build.Locator.dll`，則不需要散發其他 MSBuild 組件。

更新專案以使用 MSBuild 15 和定位器 API，需要在專案中進行一些變更，如下所述。 若要查看更新專案所需的變更範例，請參閱[對 MSBuildLocator 儲存機制中的範例專案所做的認可](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15)。

### <a name="change-msbuild-references"></a>變更 MSBuild 參考

為了確保從中央位置載入 MSBuild，您不得與應用程式一起散發其組件。

變更專案以避免從中央位置載入 MSBuild 的機制，取決於您如何參考 MSBuild。

#### <a name="using-nuget-packages-preferred"></a>使用 NuGet 套件 (慣用)

這些指示假設您使用 [`PackageReference` 樣式的 NuGet 參考](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files)。

變更您的專案檔案，以從其 NuGet 套件參考 MSBuild 組件。 指定 `ExcludeAssets=runtime` 以告訴 NuGet，只有在建置時需要組件，且不應複製到輸出目錄。

MSBuild 套件的主要和次要版本，必須小於或等於您要支援的 Visual Studio 最小版本。 如果您想要支援任何版本的 Visual Studio 2017，請參考套件版本 `15.1.548`。

例如，您可以使用這個 XML：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="using-extension-assemblies"></a>使用延伸模組組件

如果您無法使用 NuGet 套件，您可以參考與 Visual Studio 一起散發的 MSBuild 組件。 如果您直接參考 MSBuild 時，請確定它將不會複製到輸出目錄，方法是將 `Copy Local` 設定為 `False`。 在專案檔中，它會看起來如下：

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>繫結重新導向

參考 Microsoft.Build.Locator 套件，可自動確保您的應用程式使用所有版本 MSBuild 組件的必要繫結重新導向至 `15.1.0.0`。

### <a name="ensure-output-clean"></a>確定乾淨的輸出

建置您的專案，並檢查輸出目錄，以確定其中不含任何 `Microsoft.Build.*.dll` 組件 (非下一個步驟中新增的 `Microsoft.Build.Locator.dll`)。

### <a name="add-package-reference"></a>新增套件參考

新增 NuGet 套件參考至 [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/)。

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>註冊執行個體，然後呼叫 MSBuild

新增對定位程式 API 的呼叫，然後才呼叫使用 MSBuild 的任何方法。

這樣做的最簡單方式是將呼叫新增至

```c#
MSBuildLocator.RegisterDefaults();
```

您的應用程式啟動程式碼。

如果您想要對 MSBuild 載入進行細部控制，您可以選取 `MSBuildLocator.QueryVisualStudioInstances()` 的結果，以手動方式傳遞給 `MSBuildLocator.RegisterInstance()`，但通常不需要這個動作。
