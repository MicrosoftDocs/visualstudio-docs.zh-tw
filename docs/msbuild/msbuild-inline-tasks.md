---
title: MSBuild 內嵌工作 | Microsoft Docs
description: 瞭解如何藉由編譯 ITask 介面的類別來建立 MSBuild 內嵌工作。
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a90a5a251169bc9b41dea5bfddcfa2f8459af28
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919052"
---
# <a name="msbuild-inline-tasks"></a>MSBuild 內嵌工作

MSBuild 工作通常是透過編譯實作 <xref:Microsoft.Build.Framework.ITask> 介面的類別來建立。 如需詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。

 從 .NET Framework 4 版開始，您可以在專案檔中建立內嵌工作。 您不必建立個別的組件來裝載工作。 這讓您能夠更輕鬆地追蹤原始程式碼，並讓部署工作變得更容易。 原始程式碼已整合到指令碼。

 在 MSBuild 15.8 中，已新增 [RoslynCodeTaskFactory](../msbuild/msbuild-roslyncodetaskfactory.md)，以建立 .NET Standard 跨平台內嵌工作。  如果您需要在 .NET Core 上使用內嵌工作，則必須使用 RoslynCodeTaskFactory。
## <a name="the-structure-of-an-inline-task"></a>內嵌工作的結構

 內嵌工作包含於 [UsingTask](../msbuild/usingtask-element-msbuild.md) 項目中。 內嵌工作和 `UsingTask` 包含它的元素通常會包含在 *.targets* 檔案中，並視需要匯入其他專案檔。 以下是基本的內嵌工作。 請注意，它不會執行任何動作。

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="CodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 範例中的 `UsingTask` 項目具有三個描述工作的屬性，以及編譯工作的內嵌工作 Factory。

- `TaskName` 屬性會為工作命名，在此案例中為 `DoNothing`。

- `TaskFactory` 屬性會為實作內嵌工作 Factory 的類別命名。

- `AssemblyFile` 屬性會提供內嵌工作 Factory 的位置。 或者，您可以使用 `AssemblyName` 屬性來指定內嵌工作 factory 類別的完整名稱，此名稱通常位於 `$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll` 。

`DoNothing` 工作的其餘項目是空的，它們的用途是用來說明內嵌工作的順序和結構。 本主題後續內容中將提供更強固的範例。

- `ParameterGroup` 則是選擇性元素。 指定時，它將會宣告工作的參數。 如需輸入和輸出參數的詳細資訊，請參閱本主題稍後的 [輸入和輸出參數](#input-and-output-parameters) 。

- `Task` 項目會描述並包含工作原始程式碼。

- `Reference` 項目會指定您在程式碼中使用的 .NET 組件參考。 這相當於在 Visual Studio 中加入專案的參考。 `Include` 屬性會指定參考組件的路徑。

- `Using` 項目會列出您想要存取的命名空間。 這類似於 Visual C# 中的 `Using` 陳述式。 `Namespace` 屬性會指定要包含的命名空間。

`Reference` 和 `Using` 項目與語言無關。 內嵌工作可以使用任何一種受支援的 .NET CodeDom 語言來撰寫，例如：Visual Basic 或 Visual C#。

> [!NOTE]
> `Task` 項目包含的項目皆為工作 Factory (在此案例中為程式碼工作 Factory) 特定。

### <a name="code-element"></a>程式碼項目

 `Task` 項目內顯示的最後一個子項目是 `Code` 項目。 `Code` 項目會包含或尋找您想要編譯為工作的程式碼。 您放入 `Code` 項目的內容取決於您要撰寫工作的方式。

 `Language` 屬性會指定您用來撰寫程式碼的語言。 可接受的值為 `cs` (適用於 C#)、`vb` (適用於 Visual Basic)。

 `Type` 屬性會指定可在 `Code` 項目中找到的程式碼類型。

- 如果 `Type` 的值是 `Class`，則 `Code` 元素會包含衍生自 <xref:Microsoft.Build.Framework.ITask> 介面的類別程式碼。

- 如果 `Type` 的值是 `Method`，則程式碼會定義 <xref:Microsoft.Build.Framework.ITask> 介面之 `Execute` 方法的覆寫。

- 如果 `Type` 的值是 `Fragment`，則程式碼會定義 `Execute` 方法的內容，但不會定義簽章或 `return` 陳述式。

程式碼本身通常會出現在 `<![CDATA[` 標記和 `]]>` 標記之間。 因為程式碼是在 CDATA 區段中，所以您不必擔心如何轉義保留字元，例如 " \<" or "> "。

或者，您可以使用 `Code` 項目的 `Source` 屬性，來指定包含您工作程式碼的檔案位置。 原始程式檔中的程式碼必須是 `Type` 屬性所指定的類型。 如果 `Source` 屬性存在，`Type` 的預設值為 `Class`。 如果 `Source` 不存在，預設值為 `Fragment`。

> [!NOTE]
> 在原始程式檔中定義工作類別時，類別名稱必須與對應的 [UsingTask](../msbuild/usingtask-element-msbuild.md) 項目的 `TaskName` 屬性相符。

## <a name="helloworld"></a>HelloWorld

 以下是更強固的內嵌工作。 HelloWorld 工作會在預設的錯誤記錄裝置上顯示 "Hello, world!"， 此裝置通常是系統主控台或 Visual Studio 的 [輸出] 視窗。 範例所包含的 `Reference` 項目僅供說明之用。

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="CodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 您可以將 HelloWorld 工作儲存在名為 *HelloWorld* 的檔案中，然後從專案叫用它，如下所示。

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>輸入和輸出參數

 內嵌工作參數是 `ParameterGroup` 項目的子項目。 每個參數都會採用定義它的項目名稱。 下列程式碼會定義參數 `Text`。

```xml
<ParameterGroup>
  <Text />
</ParameterGroup>
```

 參數可能具備下列其中一或多個屬性：

- `Required` 是選擇性屬性，預設值為 `false`。 如果是 `true`，則為必要參數，必須為它提供值，才能呼叫工作。

- `ParameterType` 是選擇性屬性，預設值為 `System.String`。 它可能會設定為任何完整的類型，這種類型是可使用 System.Convert.ChangeType 從字串轉換或轉換自字串的項目或值。 (換句話說，就是可傳遞到外部工作或從外部工作傳入的任何類型)。

- `Output` 是選擇性屬性，預設值為 `false`。 如果是 `true`，則必須為參數提供值，才能從 Execute 方法傳回。

例如，

```xml
<ParameterGroup>
  <Expression Required="true" />
  <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
  <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

定義下列三個參數：

- `Expression` 是 System.String 類型的必要輸入參數。

- `Files` 是必要的項目清單輸入參數。

- `Tally` 是 System.Int32 類型的輸出參數。

如果 `Code` 項目具有 `Fragment` 或 `Method` 的 `Type` 屬性，則會自動為每個參數建立屬性。 否則，必須在工作原始程式碼中明確宣告屬性，而且屬性必須完全符合它們的參數定義。

## <a name="example"></a>範例

 下列內嵌工作會使用指定的值，來取代在指定檔案中出現的每一個語彙基元。

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup>
      <Path ParameterType="System.String" Required="true" />
      <Token ParameterType="System.String" Required="true" />
      <Replacement ParameterType="System.String" Required="true" />
    </ParameterGroup>
    <Task>
      <Code Type="Fragment" Language="cs"><![CDATA[
string content = File.ReadAllText(Path);
content = content.Replace(Token, Replacement);
File.WriteAllText(Path, content);

]]></Code>
    </Task>
  </UsingTask>

  <Target Name='Demo' >
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>
  </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [逐步解說：建立內嵌工作](../msbuild/walkthrough-creating-an-inline-task.md)
