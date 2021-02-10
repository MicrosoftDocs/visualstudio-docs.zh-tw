---
title: 從頭開始建立 MSBuild 專案檔
description: 逐步解說從頭開始建立 MSBuild 專案檔，以瞭解 XML 的組織方式，以及如何加以變更以控制組建。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3d0462382ddcc86a23c7e25162fb429b9f9893
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967536"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>逐步解說：從頭開始建立 MSBuild 專案檔

以 .NET Framework 為目標的程式設計語言，使用 MSBuild 專案檔描述及控制應用程式建置流程。 當您使用 Visual Studio 建立 MSBuild 專案檔時，系統會自動將適當的 XML 加入該檔案。 不過，您可能會發現，了解 XML 的組織方式，以及您如何對其進行變更以控制組建會非常有用。

 如需有關為 c + + 專案建立專案檔的詳細資訊，請參閱 [MSBuild (c + +) ](/cpp/build/msbuild-visual-cpp)。

 此逐步解說顯示如何僅使用文字編輯器以累加方式建立基本專案檔。 此逐步解說遵循下列步驟：

1. 擴充 PATH 環境變數。

2. 建立最小的應用程式原始程式檔。

3. 建立最小的 MSBuild 專案檔。

4. 使用專案檔建置應用程式。

5. 加入屬性以控制組建。

6. 透過變更屬性值來控制組建。

7. 將目標加入組建。

8. 透過指定目標來控制組建。

9. 以累加方式建置。

此逐步解說會顯示如何在命令提示字元處建置專案，並檢查結果。 如需有關 MSBuild，以及如何在命令提示字元中執行 MSBuild 的詳細資訊，請參閱[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。

若要完成本逐步解說，您必須安裝 Visual Studio，因為它包含了逐步解說所需的 MSBuild 和 Visual c # 編譯器。

## <a name="extend-the-path"></a>擴充路徑

在您可以使用 MSBuild 之前，您必須擴充 PATH 環境變數，以包含所有必要的工具。 您可以使用 **Visual Studio 的開發人員命令提示字元**。 在 Windows 工作列的 [搜尋] 方塊中，于 Windows 10 上搜尋。 若要在一般命令提示字元或腳本環境中設定環境，請在 Visual Studio 安裝的 *Common7/Tools* 子資料夾中執行 *VSDevCmd.bat* 。

## <a name="create-a-minimal-application"></a>建立最小應用程式

 本節說明如何使用文字編輯器來建立基本的 c # 應用程式原始程式檔。

1. 在命令提示字元中，流覽至您要建立應用程式的資料夾，例如 *\My Documents \\* 或 *\Desktop \\*。

2. 輸入 **Md HelloWorld** 來建立名為 *\HelloWorld \\* 的子資料夾。

3. 輸入 **cd HelloWorld**，以變更至新的資料夾。

4. 啟動 [記事本] 或其他文字編輯器，然後輸入下列程式碼。

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. 儲存此原始程式碼檔案，並將它命名為 *Helloworld.cs*。

6. 在命令提示字元中輸入 **csc helloworld.cs**，以建置應用程式。

7. 在命令提示字元中輸入 **helloworld**，以測試應用程式。

     此時應該會顯示 [Hello, world!] 訊息。

8. 在命令提示字元中輸入 **del helloworld.exe**，以刪除應用程式。

## <a name="create-a-minimal-msbuild-project-file"></a>建立最小的 MSBuild 專案檔

 既然您已具有最小的應用程式原始程式檔，您就可以建立最小的專案檔，以建置應用程式。 這個專案檔包含下列項目：

- 必要的根 `Project` 節點。

- 包含項目元素的 `ItemGroup` 節點。

- 參考應用程式原始程式檔的項目元素。

- 包含建置應用程式所需工作的 `Target` 節點。

- 啟動 Visual C# 編譯器以建置應用程式的 `Task` 項目。

### <a name="to-create-a-minimal-msbuild-project-file"></a>建立最小的 MSBuild 專案檔

1. 在文字編輯器中，使用下列兩行取代現有文字：

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. 請插入此 `ItemGroup` 節點做為 `Project` 節點的子項目：

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     請注意此 `ItemGroup` 已包含項目元素。

3. 請加入此 `Target` 節點做為 `Project` 節點的子項目。 將節點命名為 `Build`。

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. 插入此工作項目做為 `Target` 節點的子項目：

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. 儲存這個專案檔，並將它命名為 *Helloworld .csproj*。

您的最小專案檔應該類似下列程式碼：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

建置目標中的工作會循序執行。 在此情況下，Visual C# 編譯器 `Csc` 工作是唯一的工作。 它會預期要編譯的原始程式檔清單，由 `Compile` 項目的值提供。 `Compile`專案只會參考一個原始檔 *Helloworld.cs*。

> [!NOTE]
> 在 item 專案中，您可以使用星號萬用字元 (\*) 來參考副檔名為 *.cs* 的所有檔案，如下所示：
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="build-the-application"></a>建置應用程式

 現在，若要建置應用程式，請使用您剛剛建立的專案檔。

1. 在命令提示字元中，輸入 **msbuild helloworld .csproj-t:Build**。

     叫用 Visual C# 編譯器來建立 Helloworld 應用程式，即可建置 Helloworld 專案檔的建置目標。

2. 輸入 **helloworld** 來測試應用程式。

     此時應該會顯示 [Hello, world!] 訊息。

> [!NOTE]
> 提升詳細資訊層級，即可查看組建的更多詳細資料。 若要將詳細資訊層級設為「詳細」，請在命令提示字元處輸入下列命令：
>
> **msbuild helloworld .csproj-t:Build-詳細資訊：詳細**

## <a name="add-build-properties"></a>加入建置屬性

 您可以將建置屬性加入專案檔，以進一步控制組建。 立刻加入以下屬性：

- `AssemblyName` 屬性可指定應用程式的名稱。

- `OutputPath` 屬性可指定要包含應用程式的資料夾。

### <a name="to-add-build-properties"></a>加入建置屬性

1. 在命令提示字元中輸入 **del helloworld.exe**，以刪除現有的應用程式。

2. 在專案檔中，於開頭的 `PropertyGroup` 項目之後，插入此 `Project` 項目：

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. 將此工作加入建置目標之後，才能進行 `Csc` 工作：

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     `MakeDir` 工作會建立由 `OutputPath` 屬性命名的資料夾，前提是目前沒有該名稱的資料夾。

4. 將此 `OutputAssembly` 屬性加入 `Csc` 工作：

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     這會指示 Visual C# 編譯器產生由 `AssemblyName` 屬性命名的組件，並將其置於由 `OutputPath` 屬性命名的資料夾中。

5. 儲存您的變更。

您的專案檔現在應該類似下列程式碼：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> 當您在 `OutputPath` 項目中指定資料夾名稱時，建議您在資料夾名稱的結尾加入反斜線 (\\) 路徑分隔符號，而不是在 `Csc` 工作的 `OutputAssembly` 屬性中加入它。 因此，
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly="$(OutputPath)$(AssemblyName).exe" />`
>
> 勝過
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>測試建置屬性

 現在，您可以使用專案檔建置應用程式，您在該檔案中使用建置屬性來指定輸出資料夾和應用程式名稱。

1. 在命令提示字元中，輸入 **msbuild helloworld .csproj-t:Build**。

     這會建立 *\bin \\* 資料夾，然後叫用 Visual c # 編譯器來建立 *MSBuildSample* 應用程式，並將它放在 *\bin \\* 資料夾中。

2. 若要確認已 *建立 \\ \bin* 資料夾，而且它包含 *MSBuildSample* 應用程式，請輸入 **dir Bin**。

3. 輸入 **Bin\MSBuildSample** 來測試應用程式。

     此時應該會顯示 [Hello, world!] 訊息。

## <a name="add-build-targets"></a>加入建置目標

 接下來，再將兩個目標加入專案檔，如下所示：

- 用於刪除舊檔案的「清除」目標。

- 使用 `DependsOnTargets` 屬性，在「建置」工作之前強制執行「清除」工作的「重建」目標。

既然您具有多個目標，您可以將「建置」目標設為預設目標。

### <a name="to-add-build-targets"></a>加入建置目標

1. 在專案檔中，在「建置」目標之後加入這兩個目標：

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     「清除」目標會叫用「刪除」工作，以刪除應用程式。 「重建」目標會在「清除」目標和「建置」目標執行之後才執行。 雖然「重建」目標沒有工作，但它會導致「清除」目標在「建置」目標之前執行。

2. 將此 `DefaultTargets` 屬性加入開頭的 `Project` 項目：

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     這會將「建置」目標設為預設目標。

您的專案檔現在應該類似下列程式碼：

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>測試建置目標

 您可以執行新建置目標，以測試專案檔的以下功能：

- 建置預設組建。

- 在命令提示字元處設定應用程式名稱。

- 在建置其他應用程式之前，刪除應用程式。

- 刪除應用程式而不建置其他應用程式。

### <a name="to-test-the-build-targets"></a>測試建置目標

1. 在命令提示字元中，輸入 **msbuild helloworld .csproj-p:AssemblyName = 問候語**。

     因為您未使用 **-t** 參數明確地設定目標，因此 MSBuild 會執行預設的組建目標。 **-P** 參數會覆寫 `AssemblyName` 屬性，並為其提供新值 `Greetings` 。 這會導致在 *\bin \\* 資料夾中建立新的應用程式 *Greetings.exe*。

2. 若要確認 *\bin \\* 資料夾同時包含 *MSBuildSample* 應用程式和新的 *問候語* 應用程式，請輸入 **dir Bin**。

3. 輸入 **Bin\Greetings** 來測試 Greetings 應用程式。

     此時應該會顯示 [Hello, world!] 訊息。

4. 輸入 **msbuild helloworld t:clean**，以刪除 MSBuildSample 應用程式。

     這會執行 Clean 工作，以移除具有預設 `AssemblyName` 屬性值 `MSBuildSample` 的應用程式。

5. 輸入 msbuild helloworld 來刪除問候語應用程式 **。 .csproj-t:clean-p:AssemblyName = 問候語**。

     這會執行 Clean 工作，以移除具有指定 **AssemblyName** 屬性值 `Greetings` 的應用程式。

6. 若要確認 *\\ \bin* 資料夾現在是空的，請輸入 **dir Bin**。

7. 輸入 **msbuild**。

     雖然未指定專案檔，但 MSBuild 會建立 *helloworld .csproj* 檔案，因為目前的資料夾中只有一個專案檔。 這會導致在 *\bin \\* 資料夾中建立 *MSBuildSample* 應用程式。

     若要確認 *\bin \\* 資料夾包含 *MSBuildSample* 應用程式，請輸入 **dir Bin**。

## <a name="build-incrementally"></a>以累加方式建置

 您可以告知 MSBuild，僅在目標所依賴的原始程式檔或目標檔變更時，才能建置目標。 MSBuild 會使用檔案的時間戳記判定檔案是否已變更。

### <a name="to-build-incrementally"></a>以累加方式建置

1. 在專案檔中，將以下屬性加入開頭的「建置」目標：

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     這會指定「建置」目標依賴在 `Compile` 項目群組中指定的輸入檔，且輸出目標是應用程式檔。

     所產生的「建置」目標應該類似下列程式碼：

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. 在命令提示字元中輸入 **msbuild-v:d** ，以測試組建目標。

     請記住， *helloworld* 是預設的專案檔案，而該組建是預設的目標。

     **-V:d** 參數會指定組建進程的詳細描述。

     此時應該顯示下列幾行：

     **將略過目標 "Build"，因為所有輸出檔對於其輸入檔而言都已更新。**

     **輸入檔：HelloWorld.cs**

     **輸出檔：BinMSBuildSample.exe**

     MSBuild 會略過「建置」目標，因為自上次建置應用程式以來，從未變更任何原始程式檔。

## <a name="c-example"></a>C# 範例

下列範例顯示的專案檔會編譯 c # 應用程式，並記錄包含輸出檔名稱的訊息。

### <a name="code"></a>程式碼

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Visual Basic 範例

下列範例顯示的專案檔會編譯 Visual Basic 的應用程式，並記錄包含輸出檔名稱的訊息。

### <a name="code"></a>程式碼

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>接下來要做什麼？

 Visual Studio 可以自動執行本逐步解說中提及的大量工作。 若要了解如何使用 Visual Studio 建立、編輯、建置及測試 MSBuild 專案檔，請參閱[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。

## <a name="see-also"></a>另請參閱

- [MSBuild 概觀](../msbuild/msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
