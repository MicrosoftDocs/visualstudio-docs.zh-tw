---
title: 屬性函式 | Microsoft Docs
description: 瞭解如何使用屬性函式，這些函式會呼叫出現在 MSBuild 屬性定義中 .NET Framework 方法。
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c4a6254f15a4108c525231d0e5e93c6fc71bfb3
ms.sourcegitcommit: d3577395cf016f2836eb5a3c1d496cca6d449baa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2021
ms.locfileid: "110413334"
---
# <a name="property-functions"></a>屬性函式

屬性函式是呼叫出現在 MSBuild 屬性定義中 .NET Framework 方法。 與工作不同，屬性函式可用於目標外部，並在執行任何目標之前，先進行評估。

在不使用 MSBuild 工作的情況下，您可以讀取系統時間、比較字串、比對規則運算式，以及執行組建指令碼中的其他動作。 MSBuild 會嘗試將字串轉換為數字或將數字轉換為字串，並視需要進行其他轉換。

從屬性函式傳回的字串值具有逸出的[特殊字元](msbuild-special-characters.md)。 如果您想要將值視為直接放入專案檔中，請使用 `$([MSBuild]::Unescape())` 來取消逸出特殊字元。

屬性函式可搭配 .NET Framework 4 和更新版本使用。

## <a name="property-function-syntax"></a>屬性函式語法

以下是三種類型的屬性函式；每一種函式都具有不同的語法：

- 字串 (執行個體) 屬性函式
- 靜態屬性函式
- MSBuild 屬性函式

### <a name="string-property-functions"></a>字串屬性函式

所有建置屬性值都是字串值。 您可以使用字串 (執行個體) 方法操作任何屬性值。 例如，您可以使用下列程式碼，從代表完整路徑的建置屬性，擷取磁碟機名稱 (前三個字元)：

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>靜態屬性函式

在您的組建指令碼中，您可以存取許多系統類別的靜態屬性和方法。 若要取得靜態屬性的值，請使用下列語法，其中 \<Class> 是系統類別的名稱，而 \<Property> 是屬性的名稱。

```
$([Class]::Property)
```

例如，您可以使用下列程式碼，將建置屬性設為目前的日期和時間。

```xml
<Today>$([System.DateTime]::Now)</Today>
```

若要呼叫靜態方法，請使用下列語法，其中 \<Class> 是 system 類別的名稱、 \<Method> 是方法的名稱，而 (\<Parameters>) 是方法的參數清單：

```
$([Class]::Method(Parameters))
```

例如，若要將建置屬性設為新的 GUID，您可以使用下列指令碼：

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

在靜態屬性函式中，您可以使用以下系統類別的靜態方法或屬性：

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

此外，您可以使用下列靜態方法和屬性：

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System. 環境：： GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System.servicemodel. File：： GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.servicemodel. File：： GetAttributes](xref:System.IO.File.GetAttributes*)
- [System.servicemodel. File：： GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System.servicemodel. File：： GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.IO.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>在靜態屬性上呼叫執行個體方法

如果您存取的靜態屬性傳回物件執行個體，您就可以叫用該物件的執行個體方法。 若要叫用實例方法，請使用下列語法，其中 \<Class> 是系統類別的名稱、是屬性的名稱、 \<Property> \<Method> 是方法的名稱，而 (\<Parameters>) 是方法的參數清單：

```
$([Class]::Property.Method(Parameters))
```

類別的名稱必須是命名空間的完整名稱。

例如，您可以使用下列程式碼，將建置屬性設為目前日期的今天。

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild 屬性函式

您組建中的數個靜態方法可以存取來提供算術、位元邏輯和逸出字元支援。 您可以使用下列語法存取這些方法，其中 \<Method> 是方法的名稱，而 (\<Parameters>) 是方法的參數清單。

```
$([MSBuild]::Method(Parameters))
```

例如，若要將兩個具有數值的屬性加在一起，請使用下列程式碼。

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

以下是 MSBuild 屬性函式的清單：

|函式簽章|描述|
|------------------------|-----------------|
|double Add(double a, double b)|將兩個雙精度浮點數相加。|
|long Add(long a, long b)|將兩個長整數相加。|
|double Add(double a, double b)|將兩個雙精度浮點數相減。|
|long Add(long a, long b)|將兩個長整數相減。|
|double Add(double a, double b)|將兩個雙精度浮點數相乘。|
|long Multiply(long a, long b)|將兩個長整數相乘。|
|double Divide(double a, double b)|將兩個雙精度浮點數相除。|
|long Divide(long a, long b)|將兩個長整數相除。|
|double Modulo(double a, double b)|對兩個雙精度浮點數進行模數運算。|
|long Modulo(long a, long b)|對兩個長整數進行模數運算。|
|string Escape(string unescaped)|根據 MSBuild 逸出規則逸出字串。|
|string Unescape(string escaped)|根據 MSBuild 逸出規則取消逸出字串。|
|int BitwiseOr(int first, int second)|對第一和第二個整數 (第一 &#124; 第二) 執行位元 `OR`。|
|int BitwiseAnd(int first, int second)|對第一和第二個整數 (第一 & 第二) 執行位元 `AND`。|
|int BitwiseXor(int first, int second)|對第一和第二個整數 (第一 ^ 第二) 執行位元 `XOR`。|
|int BitwiseNot(int first)|執行位元 `NOT` (~第一)。|
|bool IsOsPlatform(string platformString)|指定目前的作業系統平台是否為 `platformString`。 `platformString` 必須是 <xref:System.Runtime.InteropServices.OSPlatform> 的成員。|
|bool IsOSUnixLike()|如果目前的作業系統是 UNIX 系統，則為 true。|
|string NormalizePath(params string[] path)|取得所提供路徑的規範化完整路徑，並確保它包含目前作業系統的正確目錄分隔符號字元。|
|string NormalizeDirectory(params string[] path)|取得所提供目錄的規範化完整路徑，並確保它包含目前作業系統的正確目錄分隔符號字元，且後面有斜線。|
|string EnsureTrailingSlash(string path)|如果指定的路徑後面沒有斜線，請新增一個。 如果此路徑是空字串，請不要修改它。|
|string GetPathOfFileAbove(string file, string startingDirectory)|搜尋並傳回目錄結構中檔案的完整路徑，該檔案位於目前組建檔案的位置，或根據 `startingDirectory` 指定的。|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|在指定的目錄中尋找並傳回檔案的目錄，或在該目錄上方目錄結構中的位置。|
|string MakeRelative(string basePath, string path)|讓 `path` 成為 `basePath` 的相對項。 `basePath` 必須是絕對目錄。 如果 `path` 不能成為相對的，它就會被逐字傳回。 類似於 `Uri.MakeRelativeUri`。|
|string ValueOrDefault(string conditionValue, string defaultValue)|只有當參數 'conditionValue' 為空時，才傳回參數 'defaultValue' 中的字串；否則，傳回值 conditionValue。|

## <a name="nested-property-functions"></a>巢狀屬性函式

您可以組合屬性函式，以構成較複雜的函式，如下列範例所示。

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

此範例會傳回路徑 <xref:System.IO.FileAttributes> 所提供檔案之 `Archive``tempFile` 位元 (32 或 0) 的值。 請注意，列舉資料值無法依屬性函式中的名稱顯示。 必須改為使用數值 (32)。

中繼資料也可能會出現在巢狀屬性函式中。 如需詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

MSBuild 中的 `DoesTaskHostExist` 屬性函式會傳回目前是否已為指定執行階段和架構值安裝工作主機。

此屬性函式具有下列語法：

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

MSBuild 中的 `EnsureTrailingSlash` 屬性函式會加上尾端斜線 (如果原本沒有的話)。

此屬性函式具有下列語法：

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

MSBuild `GetDirectoryNameOfFileAbove` 屬性函式會在路徑中的目前目錄上方，尋找目錄中的檔案。

 此屬性函式具有下列語法：

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 下列程式碼是此語法的範例。

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

`GetPathOfFileAbove`如果位於目前的目錄上方的目錄結構中，MSBuild 中的屬性函式會傳回指定檔案的路徑。 它在功能上相當於呼叫

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

此屬性函式具有下列語法：

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` 屬性函式會傳回登錄機碼的值。 此函式採用兩個引數 (機碼名稱和值名稱)，並傳回登錄的值。 如果您未指定值名稱，則會傳回預設值。

下列範例顯示如何使用此函式：

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

如果提供登錄機碼、值和一或多個已排序登錄檢視，MSBuild `GetRegistryValueFromView` 屬性函式會取得系統登錄資料。 在每一個登錄檢視中會按順序搜尋機碼和值，直到找到它們。

此屬性函式的語法為：

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64 位作業系統會維護 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** 登錄機碼，以呈現32位應用程式的 **HKEY_LOCAL_MACHINE\SOFTWARE** 登錄視圖。

根據預設，在 WOW64 上執行的 32 位元應用程式會存取 32 位元登錄檢視，而 64 位元應用程式會存取 64 位元登錄檢視。

下列登錄檢視皆可使用：

|登錄檢視|定義|
|-------------------|----------------|
|RegistryView.Registry32|32 位元應用程式登錄檢視。|
|RegistryView.Registry64|64 位元應用程式登錄檢視。|
|RegistryView.Default|符合應用程式執行所在之處理序的登錄檢視。|

以下是一個範例。

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

取得 **ReferenceAssemblies** 機碼的 **SLRuntimeInstallPath** 資料，首先在 64 位元登錄檢視中尋找，然後在 32 位元登錄檢視中尋找。

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` 屬性函式會傳回與第一個路徑相對之第二個路徑的相對路徑。 每一個路徑都可以是檔案或資料夾。

此屬性函式具有下列語法：

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

下列程式碼是此語法的範例。

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

MSBuild `ValueOrDefault` 屬性函式會傳回第一個引數，除非它是 null 或空白。 如果第一個引數是 null 或空白，函式會傳回第二個引數。

下列範例顯示如何使用此函式。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>MSBuild TargetFramework 和 TargetPlatform 函數

MSBuild 16.7 和更新版本定義了數個函式來處理 [TargetFramework 和 TargetPlatform 屬性](msbuild-target-framework-and-target-platform.md)。

|函式簽章|描述|
|------------------------|-----------------|
|GetTargetFrameworkIdentifier (字串 targetFramework) |從 TargetFramework 剖析 r。|
|GetTargetFrameworkVersion (字串 targetFramework) |從 TargetFramework 剖析 TargetFrameworkVersion。|
|GetTargetPlatformIdentifier (字串 targetFramework) |從 TargetFramework 剖析 r。|
|GetTargetPlatformVersion (字串 targetFramework) |從 TargetFramework 剖析 TargetPlatformVersion。|
|IsTargetFrameworkCompatible (字串 targetFrameworkTarget，字串 targetFrameworkCandidate) |如果候選目標 framework 與此目標 framework 相容，則傳回 ' True '，否則傳回 false。|

下列範例顯示如何使用這些函式。 

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::GetTargetFrameworkIdentifier('net5.0-windows7.0'))</Value1>
        <Value2>$([MSBuild]::GetTargetFrameworkVersion('net5.0-windows7.0'))</Value2>
        <Value3>$([MSBuild]::GetTargetPlatformIdentifier('net5.0-windows7.0'))</Value3>
        <Value4>$([MSBuild]::GetTargetPlatformVersion('net5.0-windows7.0'))</Value4>
        <Value5>$([MSBuild]::IsTargetFrameworkCompatible('net5.0-windows', 'net5.0'))</Value5>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
        <Message Text="Value3 = $(Value3)" />
        <Message Text="Value4 = $(Value4)" />
        <Message Text="Value5 = $(Value5)" />
    </Target>
</Project>
```

```output
Value1 = .NETCoreApp
Value2 = 5.0
Value3 = windows
Value4 = 7.0
Value5 = True
```

## <a name="msbuild-version-comparison-functions"></a>MSBuild 版本比較函數

MSBuild 16.5 和更新版本會定義數個函式來比較代表版本的字串。

> [!Note]
> 條件中的比較運算子 [可以比較可剖析為 `System.Version` 物件的字串](#msbuild-conditions.md#Comparing-versions)，但比較可能會產生非預期的結果。 偏好屬性函數。

|函式簽章|描述|
|------------------------|-----------------|
|VersionEquals (字串 a，字串 b) |`true` `a` 根據下列規則傳回版本和相等 `b` 。|
|VersionGreaterThan (字串 a，字串 b) |`true`如果版本 `a` 大於下列規則，則傳回 `b` 。|
|VersionGreaterThanOrEquals (字串 a，字串 b) |`true`如果版本 `a` 大於或等於 `b` 下列規則，則傳回。|
|VersionLessThan (字串 a，字串 b) |`true`如果版本低於 `a` 下列規則，則傳回 `b` 。|
|VersionLessThanOrEquals (字串 a，字串 b) |`true`如果版本 `a` 小於或等於下列規則，則傳回 `b` 。|
|VersionNotEquals (字串 a，字串 b) |`false` `a` 根據下列規則傳回版本和相等 `b` 。|

在這些方法中，會剖析類似的版本 <xref:System.Version?displayProperty=fullName> ，但有下列例外狀況：

* 前置 `v` 或 `V` 會被忽略，可允許與進行比較 `$(TargetFrameworkVersion)` 。

* 從第一個 '-' 或 ' + ' 到版本字串結尾的所有專案都會被忽略。 這可讓 (semver) 的語義版本傳遞，但順序與 semver 並不相同。 但是，發行前版本規範和組建中繼資料沒有任何排序權數。 這項功能很有用，例如，為了開啟功能， `>= x.y` 並讓它啟動 `x.y.z-pre` 。

* 未指定的元件與零值部分相同。 (`x == x.0 == x.0.0 == x.0.0.0`).

* 整陣列件中不允許空白字元。

* 主要版本只是有效 (`3` 等於 `3.0.0.0`) 

* `+` 不允許為整陣列件的正整數， (它會被視為 semver 中繼資料並加以忽略) 

> [!TIP]
> [TargetFramework 屬性](msbuild-target-framework-and-target-platform.md)的比較通常應該使用[IsTargetFrameworkCompatible](#MSBuild-TargetFramework-and-TargetPlatform-functions) ，而不是解壓縮和比較版本。 這可讓您比較 `TargetFramework` 和版本之間的不同 `TargetFrameworkIdentifier` 。

## <a name="msbuild-condition-functions"></a>MSBuild 條件函數

函數 `Exists` 和 `HasTrailingSlash` 不是屬性函數。 它們可與屬性搭配使用 `Condition` 。 請參閱 [MSBuild 條件](msbuild-conditions.md)。

## <a name="see-also"></a>另請參閱

- [MSBuild 屬性](../msbuild/msbuild-properties.md)

- [MSBuild 概觀](../msbuild/msbuild.md)
