---
title: 屬性函式 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ed61d1b65d03053859b5463b574432e0396449a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758357"
---
# <a name="property-functions"></a>屬性函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
在 .NET Framework 第 4 和 4.5 版中，屬性函式可用於評估 MSBuild 指令碼。 屬性函式可用於屬性出現的任何位置。 與工作不同，屬性函式可用於目標外部，並在執行任何目標之前，先進行評估。  
  
 在不使用 MSBuild 工作的情況下，您可以讀取系統時間、比較字串、比對規則運算式，以及執行組建指令碼中的其他動作。 MSBuild 會嘗試將字串轉換為數字或將數字轉換為字串，並視需要進行其他轉換。  
  
 **本主題內容：**  
  
-   [屬性函式語法](#BKMK_Syntax)  
  
    -   [字串屬性函式](#BKMK_String)  
  
    -   [靜態屬性函式](#BKMK_Static)  
  
    -   [在靜態屬性上呼叫執行個體方法](#BKMK_InstanceMethods)  
  
    -   [MSBuild 屬性函式](#BKMK_PropertyFunctions)  
  
-   [巢狀屬性函式](#BKMK_Nested)  
  
-   [MSBuild DoesTaskHostExist](#BKMK_DoesTaskHostExist)  
  
-   [MSBuild GetDirectoryNameOfFileAbove](#BKMK_GetDirectoryNameOfFileAbove)  
  
-   [MSBuild GetRegistryValue](#BKMK_GetRegistryValue)  
  
-   [MSBuild GetRegistryValueFromView](#BKMK_GetRegistryValueFromView)  
  
-   [MSBuild MakeRelative](#BKMK_MakeRelative)  
  
-   [MSBuild ValueOrDefault](#BKMK_ValueOrDefault)  
  
##  <a name="BKMK_Syntax"></a> 屬性函式語法  
 以下是三種類型的屬性函式；每一種函式都具有不同的語法：  
  
-   字串 (執行個體) 屬性函式  
  
-   靜態屬性函式  
  
-   MSBuild 屬性函式  
  
###  <a name="BKMK_String"></a> 字串屬性函式  
 所有建置屬性值都是字串值。 您可以使用字串 (執行個體) 方法操作任何屬性值。 例如，您可以使用下列程式碼，從代表完整路徑的建置屬性，擷取磁碟機名稱 (前三個字元)：  
  
 `$(ProjectOutputFolder.Substring(0,3))`  
  
###  <a name="BKMK_Static"></a> 靜態屬性函式  
 在您的組建指令碼中，您可以存取許多系統類別的靜態屬性和方法。 若要取得靜態屬性的值，請使用下列語法，其中 *Class* 是系統類別的名稱，而 *Property* 是屬性的名稱。  
  
 `$([Class]::Property)`  
  
 例如，您可以使用下列程式碼，將建置屬性設為目前的日期和時間。  
  
 `<Today>$([System.DateTime]::Now)</Today>`  
  
 若要呼叫靜態方法，請使用下列語法，其中 *Class* 是系統類別的名稱、*Method* 是方法的名稱，而 *(Parameters)* 是方法的參數清單：  
  
 `$([Class]::Method(Parameters))`  
  
 例如，若要將建置屬性設為新的 GUID，您可以使用下列指令碼：  
  
 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  
  
 在靜態屬性函式中，您可以使用以下系統類別的靜態方法或屬性：  
  
- System.Byte  
  
- System.Char  
  
- System.Convert  
  
- System.DateTime  
  
- System.Decimal  
  
- System.Double  
  
- System.Enum  
  
- System.Guid  
  
- System.Int16  
  
- System.Int32  
  
- System.Int64  
  
- System.IO.Path  
  
- System.Math  
  
- System.UInt16  
  
- System.UInt32  
  
- System.UInt64  
  
- System.SByte  
  
- System.Single  
  
- System.String  
  
- System.StringComparer  
  
- System.TimeSpan  
  
- System.Text.RegularExpressions.Regex  
  
- Microsoft.Build.Utilities.ToolLocationHelper  
  
  此外，您可以使用下列靜態方法和屬性：  
  
- System.Environment::CommandLine  
  
- System.Environment::ExpandEnvironmentVariables  
  
- System.Environment::GetEnvironmentVariable  
  
- System.Environment::GetEnvironmentVariables  
  
- System.Environment::GetFolderPath  
  
- System.Environment::GetLogicalDrives  
  
- System.IO.Directory::GetDirectories  
  
- System.IO.Directory::GetFiles  
  
- System.IO.Directory::GetLastAccessTime  
  
- System.IO.Directory::GetLastWriteTime  
  
- System.IO.Directory::GetParent  
  
- System.IO.File::Exists  
  
- System.IO.File::GetCreationTime  
  
- System.IO.File::GetAttributes  
  
- System.IO.File::GetLastAccessTime  
  
- System.IO.File::GetLastWriteTime  
  
- System.IO.File::ReadAllText  
  
###  <a name="BKMK_InstanceMethods"></a> 在靜態屬性上呼叫執行個體方法  
 如果您存取的靜態屬性傳回物件執行個體，您就可以叫用該物件的執行個體方法。 若要叫用執行個體方法，請使用下列語法，其中 *Class* 是系統類別的名稱、*Property* 是屬性的名稱、*Method* 是方法的名稱，而 *(Parameters)* 是方法的參數清單：  
  
 `$([Class]::Property.Method(Parameters))`  
  
 類別的名稱必須是命名空間的完整名稱。  
  
 例如，您可以使用下列程式碼，將建置屬性設為目前日期的今天。  
  
 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  
  
###  <a name="BKMK_PropertyFunctions"></a> MSBuild 屬性函式  
 您組建中的數個靜態方法可以存取來提供算術、位元邏輯和逸出字元支援。 您可以使用下列語法存取這些方法，其中 *Method* 是方法的名稱，而 *Parameters* 是方法的參數清單。  
  
 `$([MSBuild]::Method(Parameters))`  
  
 例如，若要將兩個具有數值的屬性加在一起，請使用下列程式碼。  
  
 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  
  
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
  
##  <a name="BKMK_Nested"></a> 巢狀屬性函式  
 您可以組合屬性函式，以構成較複雜的函式，如下列範例所示。  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 此範例會傳回路徑 <xref:System.IO.FileAttributes> 所提供檔案之 `Archive``tempFile` 位元 (32 或 0) 的值。 請注意，列舉資料值無法依屬性函式中的名稱顯示。 必須改為使用數值 (32)。  
  
 中繼資料也可能會出現在巢狀屬性函式中。 如需詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。  
  
##  <a name="BKMK_DoesTaskHostExist"></a> MSBuild DoesTaskHostExist  
 MSBuild 中的 `DoesTaskHostExist` 屬性函式會傳回目前是否已為指定執行階段和架構值安裝工作主機。  
  
 此屬性函式具有下列語法：  
  
```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  
  
##  <a name="BKMK_GetDirectoryNameOfFileAbove"></a> MSBuild GetDirectoryNameOfFileAbove  
 MSBuild `GetDirectoryNameOfFileAbove` 屬性函式會在路徑中的目前目錄上方，尋找目錄中的檔案。  
  
 此屬性函式具有下列語法：  
  
```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  
  
 下列程式碼是此語法的範例。  
  
```  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  
  
##  <a name="BKMK_GetRegistryValue"></a> MSBuild GetRegistryValue  
 MSBuild `GetRegistryValue` 屬性函式會傳回登錄機碼的值。 此函式採用兩個引數 (機碼名稱和值名稱)，並傳回登錄的值。 如果您未指定值名稱，則會傳回預設值。  
  
 下列範例顯示如何使用此函式：  
  
```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  
  
```  
  
##  <a name="BKMK_GetRegistryValueFromView"></a> MSBuild GetRegistryValueFromView  
 如果提供登錄機碼、值和一或多個已排序登錄檢視，MSBuild `GetRegistryValueFromView` 屬性函式會取得系統登錄資料。 在每一個登錄檢視中會按順序搜尋機碼和值，直到找到它們。  
  
 此屬性函式的語法為：  
  
 [MSBuild\]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)  
  
 Windows 64 位元作業系統會維護 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node 登錄機碼，以代表 32 位元應用程式的 HKEY_LOCAL_MACHINE\SOFTWARE 登錄檢視。  
  
 根據預設，在 WOW64 上執行的 32 位元應用程式會存取 32 位元登錄檢視，而 64 位元應用程式會存取 64 位元登錄檢視。  
  
 下列登錄檢視皆可使用：  
  
|登錄檢視|定義|  
|-------------------|----------------|  
|RegistryView.Registry32|32 位元應用程式登錄檢視。|  
|RegistryView.Registry64|64 位元應用程式登錄檢視。|  
|RegistryView.Default|符合應用程式執行所在之處理序的登錄檢視。|  
  
 下列為範例。  
  
 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  
  
 會取得 ReferenceAssemblies 機碼的 SLRuntimeInstallPath 資料，首先在 64 位元登錄檢視中尋找，然後在 32 位元登錄檢視中尋找。  
  
##  <a name="BKMK_MakeRelative"></a> MSBuild MakeRelative  
 MSBuild `MakeRelative` 屬性函式會傳回與第一個路徑相對之第二個路徑的相對路徑。 每一個路徑都可以是檔案或資料夾。  
  
 此屬性函式具有下列語法：  
  
```  
$[MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2))  
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
  
##  <a name="BKMK_ValueOrDefault"></a> MSBuild ValueOrDefault  
 MSBuild `ValueOrDefault` 屬性函式會傳回第一個引數，除非它是 null 或空白。 如果第一個引數是 null 或空白，函式會傳回第二個引數。  
  
 下列範例顯示如何使用此函式。  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>  
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>  
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

## <a name="see-also"></a>請參閱
[MSBuild 屬性](msbuild-properties1.md)   
[MSBuild 概觀](msbuild.md)
