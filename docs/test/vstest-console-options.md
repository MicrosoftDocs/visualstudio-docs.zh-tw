---
title: VSTest.Console.exe 命令列選項
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8264aebcbced16f95c177d255e226cfffdbee0ce
ms.sourcegitcommit: 363f3e6e30dd54366ade0d08920755da5951535c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86869590"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe 命令列選項

*VSTest.Console.exe* 是用來執行測試的命令列工具。 您可以依照任何順序在命令列中指定數個選項。 這些選項列在[一般命令列選項](#general-command-line-options)中。

> [!NOTE]
> 基於相容性，Visual Studio 的 MSTest 配接器也可以在舊版模式下運作 (相當於使用 *mstest.exe* 執行測試)。 但在舊版模式下，它無法利用 TestCaseFilter 功能。 已指定 *testsettings* 檔案、*runsettings* 檔案中的 **forcelegacymode** 設定為 **true**，或使用如 **HostType** 等屬性時，配接器可以切換到舊版模式。
>
> 若要在 ARM 架構電腦上執行自動化測試，您必須使用 *VSTest.Console.exe*。

開啟[開發人員命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)以使用命令列工具，或者您可以在 *% Program Files （x86）% \ Microsoft Visual Studio \\<版本 \> \\<版本 \> \common7\ide\CommonExtensions \\<Platform 中找到此工具 |Microsoft>*。

## <a name="general-command-line-options"></a>一般命令列選項

下表列出 *VSTest.Console.exe* 的所有選項，以及選項的簡短描述。 在命令列鍵入 `VSTest.Console/?` 也能看到類似的摘要。

| 選項 | 描述 |
|---|---|
|**[*test file names*]**|從指定的檔案執行測試。 以空格分隔多個測試檔案名稱。<br />範例：`mytestproject.dll`、`mytestproject.dll myothertestproject.exe`|
|**/Settings:[*file name*]**|使用像資料收集器之類的其他設定執行測試。 如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)<br />範例： `/Settings:local.runsettings`|
|**/Tests:[*test name*]**|執行測試，其名稱包含所提供的值。 若要提供多個值，請使用逗號來區隔。<br />範例： `/Tests:TestMethod1,testMethod2`<br />**/Tests** 命令列選項無法與 **/TestCaseFilter** 命令列選項搭配使用。|
|**/Parallel**|指定以平行方式執行測試。 根據預設，最多可以使用電腦上所有可用的核心。 您可以設定要在設定檔中使用的核心數。|
|**/Enablecodecoverage**|在測試回合中啟用資料診斷配接器 CodeCoverage。<br />如果沒有使用設定檔來指定，則使用預設設定。|
|**/InIsolation**|在獨立的處理序中執行測試。<br />這種隔離會降低 *vstest.console.exe* 處理序在測試中錯誤處停止的可能性，但是測試的速度可能會比較慢。|
|**/UseVsixExtensions**|此選項可讓 *vstest.console.exe* 處理序使用或略過測試回合中已安裝的 VSIX 延伸模組 (若有的話)。<br />這個選項已被取代。 從 Visual Studio 的下一個主要版本開始，就可能會移除這個選項。 移至以 NuGet 套件形式提供的取用延伸模組。<br />範例： `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*path*]**|強制 *vstest.console.exe* 處理序在測試回合中使用來自指定路徑 (若有的話) 的自訂測試配接器。<br />範例： `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*platform type*]**|要用於測試執行的目標平台架構。<br />有效值為 x86、x64 和 ARM。|
|**/Framework: [*framework version*]**|要用於測試執行的目標 .NET 版本。<br />範例值為 `Framework35`、`Framework40`、`Framework45`、`FrameworkUap10`、`.NETCoreApp,Version=v1.1`。<br />TargetFrameworkAttribute 是用來從您的元件自動偵測這個選項，而 `Framework40` 當屬性不存在時，預設值為。 如果您從 .NET Core 元件中移除[TargetFrameworkAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.versioning.targetframeworkattribute) ，則必須明確指定此選項。<br />如果將目標 framework 指定為**Framework35**，則測試會在 CLR 4.0 「相容性模式」中執行。<br />範例： `/Framework:framework40`|
|**/TestCaseFilter:[*expression*]**|執行符合指定之運算式的測試。<br /><Expression\> 的格式為 <property\>=<value\>[\|<Expression\>]。<br />範例： `/TestCaseFilter:"Priority=1"`<br />範例： `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />**/TestCaseFilter** 命令列選項無法與 **/Tests** 命令列選項搭配使用。 <br />如需建立和使用運算式的資訊，請參閱 [ 篩選](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。|
|**/?**|顯示使用資訊。|
|**/Logger:[*uri/friendlyname*]**|指定測試結果的記錄器。 請多次指定參數，以啟用多個記錄器。<br />範例：若要將結果記錄到 Visual Studio 測試結果檔案（.TRX），請使用<br />**/Logger： .trx**<br />**[;LogFileName = \<Defaults to unique file name> ]**|
|**/ListTests:[*file name*]**|列出從指定之測試容器探索到的測試。|
|**/ListDiscoverers**|列出已安裝的測試探索程式。|
|**/ListExecutors**|列出已安裝的測試執行程式。|
|**/ListLoggers**|列出已安裝的測試記錄器。|
|**/ListSettingsProviders**|列出已安裝的測試設定提供者。|
|**/Blame**|在歸責模式下執行測試。 此選項有助於隔離導致測試主控制項損毀的問題測試。 當偵測到損毀時，它會在中建立一個序列檔案 `TestResults/<Guid>/<Guid>_Sequence.xml` ，以捕捉損毀前執行的測試順序。 如需詳細資訊，請參閱[推諉資料收集器](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md)。|
|**/Diag:[*file name*]**|將診斷追蹤記錄寫入至指定的檔案。|
|**/ResultsDirectory:[*path*]**|如果測試結果目錄不存在，則會在指定的路徑中建立該目錄。<br />範例： `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|父處理序的處理序識別碼，該父處理序負責啟動目前處理序。|
|**/Port:[*port*]**|通訊端連線和接收事件訊息的連接埠。|
|**/Collect:[*dataCollector friendlyName*]**|測試回合啟用資料收集器。 [詳細資訊](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md)。|

> [!TIP]
> 選項和值不區分大小寫。

## <a name="examples"></a>範例

執行*vstest.console.exe*的語法為：

`vstest.console.exe [TestFileNames] [Options]`

下列命令會針對測試程式庫*myTestProject.dll*執行*vstest.console.exe* ：

```cmd
vstest.console.exe myTestProject.dll
```

下列命令會使用多個測試檔案執行*vstest.console.exe* 。 以空格分隔測試檔案名稱：

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

下列命令會以數個選項執行*vstest.console.exe* 。 它會以隔離的處理序執行 *myTestFile.dll* 檔案中的測試，並使用 *Local.RunSettings* 檔案中指定的設定。 此外，它只會執行標記為 "Priority=1" 的測試，並將結果記錄到 *.trx* 檔案中。

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

下列命令會使用*vstest.console.exe* `/blame` 測試程式庫*myTestProject.dll*的選項來執行vstest.console.exe：

```cmd
vstest.console.exe myTestFile.dll /blame
```

如果發生測試主機損毀，就會產生*sequence.xml*檔案。 檔案會在其執行順序中包含測試的完整名稱，包括當機時所執行的特定測試。

如果沒有測試主機損毀，將不會產生*sequence.xml*檔案。

產生的*sequence.xml*檔案範例： 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
