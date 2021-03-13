---
title: 更新為 MSTestV2
description: 瞭解如何從 MSTestV1 更新為 MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366253"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>從 MSTestV1 升級至 MSTestV2

您可以將 *.csproj* 中所參考的 MSTest 版本從 MSTestV1 重定目標至 MSTestV2，以升級您的測試專案。 並非 MSTestV1 中的所有功能都已轉移到 MSTestV2 中，因此可能需要進行一些變更才能解決錯誤。 請參閱 [MSTestV2 中不支援的 MSTestV1 功能](#mstestv1-features-that-are-not-supported-in-mstestv2) ，以瞭解哪些功能將無法再運作。 其中有些可能需要從您的測試中移除。

1. 從單元測試專案中移除 VisualStudio. [Microsoft.visualstudio.qualitytools.webtestframework. Microsoft.visualstudio.qualitytools.unittestframework 的元件參考。
2. 將 NuGet 套件參考新增至 MSTestV2，包括 [TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) 和 nuget.org 上的 [mstest mstest.testadapter](https://www.nuget.org/packages/MSTest.TestAdapter/) 套件。您可以使用下列命令，在 NuGet 套件管理員主控台中安裝套件：

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>舊樣式的 .csproj 範例

範例 *.csproj* 目標 MSTestV1：

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

範例 *.csproj* 現在以 MSTestV2 為目標：

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> 自動程式碼 UI 測試或 Web 負載測試的測試專案與 MSTestV2 不相容。 這些專案類型已被取代。 深入瞭解自動程式 [代碼 UI 測試](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) 取代和 [Web 負載測試](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)取代。

### <a name="sdk-style-csproj-net-core-and-net-5"></a>SDK 樣式的 .csproj ( .NET Core 和 .NET 5) 

如果您的 *.csproj* 是較新的 SDK 樣式 *.csproj* ，您很可能已經使用 MSTestV2。 您可以在 NuGet 上找到適用于 [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) 和 [MSTestV2 介面卡](https://www.nuget.org/packages/MSTest.TestAdapter/) 的 nuget 套件。

範例：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>為何要升級至 MSTestV2？

在2016中，我們發行了使用 MSTestV2 發展 MSTest 架構的下一步。 您可以在公告 [blog 文章](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)中閱讀更多有關這項變更的資訊。

* 因為 MSTestV2 是以 [NuGet 套件](https://www.nuget.org/packages/MSTest.TestFramework/)的形式提供，所以更容易取得和更新。
* MSTestV2 是 [開放原始](https://github.com/microsoft/testfx)碼。
* 統一應用程式平臺支援– MSTestV2 是一種交集的執行，可在 .NET Framework、.NET Core、ASP.NET Core 和 UWP 之間提供統一的應用程式平臺支援。 [閱讀其他資訊](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/)。
* 此實作為完全跨平臺 (Windows、Linux、Mac) 。 [閱讀其他資訊](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/)。
* MSTestV2 支援以 .NET Framework 4.5.0 和更新版本為目標，.NET Core 1.0 和更新版本 (通用 Windows 應用程式 10 +) 、ASP.NET Core 1.0 和更新版本，以及 .NET 5 和更新版本。
* 提供統一的單一終端使用者擴充性機制。 [閱讀其他資訊](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/)。
* `DataRow`針對所有 MSTest 測試專案提供統一的支援。 [閱讀其他資訊](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/)。
* 可將 `TestCategory` 屬性放在類別或元件層級。 [閱讀其他資訊](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/)。
* 現在已從衍生的測試類別探索並執行從其他元件中定義之基類的測試方法。 這項變更會對衍生的測試類別類型帶來一致的行為。 如果基於相容性原因不需要此行為，則可以使用下列回合設定來變更：

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* 透過內部 [元件平行執行](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) 測試，讓您更精細地控制平行執行。 這可讓您平行執行元件中的測試。
* `TestCleanup`上的方法會被叫用， `TestClass` 即使其對應的 `TestInitialize` 方法失敗。 [問題詳細資料](https://github.com/Microsoft/testfx/issues/250)。
* 花費的時間 `AssemblyInitialize` `ClassInitialize` 不會計入測試持續時間。 這種變更會限制其對測試超時的影響。
* 無法執行的測試可以設定為透過標記標記為失敗 `MapNotRunnableToFailed` ，這是檔案中介面卡節點的一部分 `.runsettings` 。

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>MSTestV2 不支援的 MSTestV1 功能

*   測試不能包含在「已排序的測試」中。
*   介面卡不支援透過 *.testsettings* 檔案進行設定。 使用新的 [ *.runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)檔案進行測試回合設定。
*   介面卡不支援指定為 *vsmdi* 檔案的測試清單。
*   不支援 [自動程式化 UI 測試專案] 和 [Web 效能和負載測試專案] 類型。 深入瞭解自動程式 [代碼 UI 測試](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) 取代和 [Web 負載測試](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)取代。

## <a name="see-also"></a>另請參閱

- [使用設定測試回合 `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [使用測試總管進行偵錯單元測試](../test/debug-unit-tests-with-test-explorer.md)
