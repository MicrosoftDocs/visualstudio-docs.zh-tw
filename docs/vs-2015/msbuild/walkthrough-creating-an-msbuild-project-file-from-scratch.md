---
title: 逐步解說：從頭開始建立 MSBuild 專案檔案 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a77c390dd0934b0f02320080765765163a8afb93
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445608"
---
# <a name="walkthrough-creating-an-msbuild-project-file-from-scratch"></a>逐步解說：從頭開始建立 MSBuild 專案檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以 .NET Framework 為目標的程式設計語言，使用 MSBuild 專案檔描述及控制應用程式建置流程。 當您使用 Visual Studio 建立 MSBuild 專案檔時，系統會自動將適當的 XML 加入該檔案。 不過，您可能會發現，了解 XML 的組織方式，以及您如何對其進行變更以控制組建會非常有用。  
  
 如需為 C++ 專案建立專案檔的相關資訊，請參閱 [MSBuild (Visual C++)](http://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560)。  
  
 此逐步解說顯示如何僅使用文字編輯器以累加方式建立基本專案檔。 此逐步解說遵循下列步驟：  
  
- 建立最小的應用程式原始程式檔。  
  
- 建立最小的 MSBuild 專案檔。  
  
- 擴充 PATH 環境變數以包括 MSBuild。  
  
- 使用專案檔建置應用程式。  
  
- 加入屬性以控制組建。  
  
- 透過變更屬性值來控制組建。  
  
- 將目標加入組建。  
  
- 透過指定目標來控制組建。  
  
- 以累加方式建置。  
  
  此逐步解說會顯示如何在命令提示字元處建置專案，並檢查結果。 如需 MSBuild 的詳細資訊，以及如何在命令提示字元中執行 MSBuild，請參閱[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。  
  
  若要完成逐步解說，您必須已安裝 .NET Framework (2.0、3.5、4.0 或 4.5 版)，因為它包含此逐步解說所需的 MSBuild 和 Visual C# 編譯器。  
  
## <a name="creating-a-minimal-application"></a>建立最小應用程式  
 本節顯示如何使用文字編輯器建立最小 Visual C# 應用程式原始程式檔。  
  
#### <a name="to-create-the-minimal-application"></a>建立最小應用程式  
  
1. 在命令提示字元中，瀏覽至您要建立應用程式的資料夾，例如 \My Documents\ 或 \Desktop\\。  
  
2. 輸入 **md HelloWorld**，以建立名為 \HelloWorld\\ 的子資料夾。  
  
3. 輸入 **cd HelloWorld**，以變更至新的資料夾。  
  
4. 啟動 [記事本] 或其他文字編輯器，然後輸入下列程式碼。  
  
    ```  
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
  
5. 儲存此原始程式碼檔，並將其命名為 Helloworld.cs。  
  
6. 在命令提示字元中輸入 **csc helloworld.cs**，以建置應用程式。  
  
7. 在命令提示字元中輸入 **helloworld**，以測試應用程式。  
  
     此時應該會顯示 [Hello, world!] 訊息。  
  
8. 在命令提示字元中輸入**del helloworld.exe**，以刪除應用程式。  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>建立最小的 MSBuild 專案檔  
 既然您已具有最小的應用程式原始程式檔，您就可以建立最小的專案檔，以建置應用程式。 這個專案檔包含下列項目：  
  
- 必要的根 `Project` 節點。  
  
- 包含項目元素的 `ItemGroup` 節點。  
  
- 參考應用程式原始程式檔的項目元素。  
  
- 包含建置應用程式所需工作的 `Target` 節點。  
  
- 啟動 Visual C# 編譯器以建置應用程式的 `Task` 項目。  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>建立最小的 MSBuild 專案檔  
  
1. 在文字編輯器中，使用下列兩行取代現有文字：  
  
   ```  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   </Project>  
   ```  
  
2. 請插入此 `ItemGroup` 節點做為 `Project` 節點的子項目：  
  
   ```  
   <ItemGroup>  
     <Compile Include="helloworld.cs" />  
   </ItemGroup>  
   ```  
  
    請注意此 `ItemGroup` 已包含項目元素。  
  
3. 請加入此 `Target` 節點做為 `Project` 節點的子項目。 將節點命名為 `Build`。  
  
   ```  
   <Target Name="Build">  
   </Target>  
   ```  
  
4. 插入此工作項目做為 `Target` 節點的子項目：  
  
   ```  
   <Csc Sources="@(Compile)"/>  
   ```  
  
5. 儲存此專案檔，並將其命名為 Helloworld.csproj。  
  
   您的最小專案檔應該類似下列程式碼：  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  
  
 建置目標中的工作會循序執行。 在此情況下，Visual C# 編譯器 `Csc` 工作是唯一的工作。 它會預期要編譯的原始程式檔清單，由 `Compile` 項目的值提供。 `Compile` 項目僅參考一個原始程式檔 Helloworld.cs。  
  
> [!NOTE]
> 在項目元素中，您可以使用星號萬用字元 (*) 參考副檔名為 .cs 的所有檔案，如下所示：  
>   
> `<Compile Include="*.cs" />`  
>   
> 不過，建議您不要使用萬用字元，因為加入或刪除原始程式檔時，它會使得偵錯及選擇性目標變得更困難。  
  
## <a name="extending-the-path-to-include-msbuild"></a>擴充路徑以包括 MSBuild  
 在您可以存取 MSBuild 之前，您必須擴充 PATH 環境變數，以包括 .NET Framework 資料夾。  
  
#### <a name="to-add-msbuild-to-your-path"></a>將 MSBuild 加入路徑  
  
- 從 Visual Studio 2013 開始，您可以在 MSBuild 資料夾 (在 32 位元作業系統上為 `%ProgramFiles%\MSBuild`，在 64 位元作業系統上為 `%ProgramFiles(x86)%\MSBuild`) 中尋找 MSBuild.exe。  
  
     在命令提示字元中，輸入 **set PATH=%PATH%;%ProgramFiles%\MSBuild** 或 **set PATH=%PATH%;%ProgramFiles(x86)%\MSBuild**。  
  
     或者，如果您已安裝 Visual Studio，您可以使用 [Visual Studio 命令提示字元]，其中具有包括 MSBuild 資料夾的路徑。  
  
## <a name="using-the-project-file-to-build-the-application"></a>使用專案檔建置應用程式  
 現在，若要建置應用程式，請使用您剛剛建立的專案檔。  
  
#### <a name="to-build-the-application"></a>建置應用程式  
  
1. 在命令提示字元中，輸入 **msbuild helloworld.csproj /t: build**。  
  
     叫用 Visual C# 編譯器來建立 Helloworld 應用程式，即可建置 Helloworld 專案檔的建置目標。  
  
2. 輸入 **helloworld** 來測試應用程式。  
  
     此時應該會顯示 [Hello, world!] 訊息。  
  
> [!NOTE]
> 提升詳細資訊層級，即可查看組建的更多詳細資料。 若要將詳細資訊層級設為「詳細」，請在命令提示字元處輸入下列任何一個命令：  
>   
> **msbuild helloworld.csproj /t:Build /verbosity:detailed**  
  
## <a name="adding-build-properties"></a>加入建置屬性  
 您可以將建置屬性加入專案檔，以進一步控制組建。 立刻加入以下屬性：  
  
- `AssemblyName` 屬性可指定應用程式的名稱。  
  
- `OutputPath` 屬性可指定要包含應用程式的資料夾。  
  
#### <a name="to-add-build-properties"></a>加入建置屬性  
  
1. 在命令提示字元中輸入**del helloworld.exe**，以刪除現有的應用程式。  
  
2. 在專案檔中，於開頭的 `PropertyGroup` 項目之後，插入此 `Project` 項目：  
  
   ```  
   <PropertyGroup>  
     <AssemblyName>MSBuildSample</AssemblyName>  
     <OutputPath>Bin\</OutputPath>  
   </PropertyGroup>  
   ```  
  
3. 將此工作加入建置目標之後，才能進行 `Csc` 工作：  
  
   ```  
   <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
   ```  
  
    `MakeDir` 工作會建立由 `OutputPath` 屬性命名的資料夾，前提是目前沒有該名稱的資料夾。  
  
4. 將此 `OutputAssembly` 屬性加入 `Csc` 工作：  
  
   ```  
   <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
   ```  
  
    這會指示 Visual C# 編譯器產生由 `AssemblyName` 屬性命名的組件，並將其置於由 `OutputPath` 屬性命名的資料夾中。  
  
5. 儲存您的變更。  
  
   您的專案檔現在應該類似下列程式碼：  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
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
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
> 勝過  
>   
> `<OutputPath>Bin</OutputPath>`  
>   
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="testing-the-build-properties"></a>測試建置屬性  
 現在，您可以使用專案檔建置應用程式，您在該檔案中使用建置屬性來指定輸出資料夾和應用程式名稱。  
  
#### <a name="to-test-the-build-properties"></a>測試建置屬性  
  
1. 在命令提示字元中，輸入 **msbuild helloworld.csproj /t: build**。  
  
     這會建立 \Bin\ 資料夾，然後叫用 Visual C# 編譯器，即可建立 MSBuildSample 應用程式，並將其置於 \Bin\ 資料夾中。  
  
2. 若要驗證已建立 \Bin\ 資料夾，且其包含 MSBuildSample 應用程式，請輸入 **dir Bin**。  
  
3. 輸入 **Bin\MSBuildSample** 來測試應用程式。  
  
     此時應該會顯示 [Hello, world!] 訊息。  
  
## <a name="adding-build-targets"></a>加入建置目標  
 接下來，再將兩個目標加入專案檔，如下所示：  
  
- 用於刪除舊檔案的「清除」目標。  
  
- 使用 `DependsOnTargets` 屬性，在「建置」工作之前強制執行「清除」工作的「重建」目標。  
  
  既然您具有多個目標，您可以將「建置」目標設為預設目標。  
  
#### <a name="to-add-build-targets"></a>加入建置目標  
  
1. 在專案檔中，在「建置」目標之後加入這兩個目標：  
  
   ```  
   <Target Name="Clean" >  
     <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
   </Target>  
   <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
   ```  
  
    「清除」目標會叫用「刪除」工作，以刪除應用程式。 「重建」目標會在「清除」目標和「建置」目標執行之後才執行。 雖然「重建」目標沒有工作，但它會導致「清除」目標在「建置」目標之前執行。  
  
2. 將此 `DefaultTargets` 屬性加入開頭的 `Project` 項目：  
  
   ```  
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   ```  
  
    這會將「建置」目標設為預設目標。  
  
   您的專案檔現在應該類似下列程式碼：  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
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
  
## <a name="testing-the-build-targets"></a>測試建置目標  
 您可以執行新建置目標，以測試專案檔的以下功能：  
  
- 建置預設組建。  
  
- 在命令提示字元處設定應用程式名稱。  
  
- 在建置其他應用程式之前，刪除應用程式。  
  
- 刪除應用程式而不建置其他應用程式。  
  
#### <a name="to-test-the-build-targets"></a>測試建置目標  
  
1. 在命令提示字元中，輸入 **msbuild helloworld.csproj /p:AssemblyName=Greetings**。  
  
     由於您未使用 **/t** 參數來明確地設定目標，因此 MSBuild 會執行預設的 Build 目標。 **/p** 參數會覆寫 `AssemblyName` 屬性，並為其提供新值 `Greetings`。 這會在 \Bin\ 資料夾中建立新的應用程式 Greetings.exe。  
  
2. 若要驗證 \Bin\ 資料夾包含 MSBuildSample 應用程式和新的 Greetings 應用程式，請輸入 **dir Bin**。  
  
3. 輸入 **Bin\Greetings** 來測試 Greetings 應用程式。  
  
     此時應該會顯示 [Hello, world!] 訊息。  
  
4. 輸入 **msbuild helloworld.csproj /t:clean** 來刪除 MSBuildSample 應用程式。  
  
     這會執行 Clean 工作，以移除具有預設 `AssemblyName` 屬性值 `MSBuildSample` 的應用程式。  
  
5. 輸入 **msbuild helloworld.csproj /t:clean /p:AssemblyName=Greetings** 來刪除 Greetings 應用程式。  
  
     這會執行 Clean 工作，以移除具有指定 **AssemblyName** 屬性值 `Greetings` 的應用程式。  
  
6. 若要驗證 \Bin\ 資料夾現在是空的，請輸入 **dir Bin**。  
  
7. 輸入 **msbuild**。  
  
     雖然沒有指定專案檔，但 MSBuild 仍會建置 helloworld.csproj 檔案，因為在目前的資料夾中，只有一個專案檔。 這會在 \Bin\ 資料夾中建立 MSBuildSample 應用程式。  
  
     若要驗證 \Bin\ 資料夾包含 MSBuildSample 應用程式，請輸入 **dir Bin**。  
  
## <a name="building-incrementally"></a>以累加方式建置  
 您可以告知 MSBuild，僅在目標所依賴的原始程式檔或目標檔變更時，才能建置目標。 MSBuild 會使用檔案的時間戳記判定檔案是否已變更。  
  
#### <a name="to-build-incrementally"></a>以累加方式建置  
  
1. 在專案檔中，將以下屬性加入開頭的「建置」目標：  
  
    ```  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     這會指定「建置」目標依賴在 `Compile` 項目群組中指定的輸入檔，且輸出目標是應用程式檔。  
  
     所產生的「建置」目標應該類似下列程式碼：  
  
    ```  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2. 在命令提示字元中輸入 **msbuild /v:d**，以測試 Build 目標。  
  
     請記住，helloworld.csproj 是預設專案檔，而該「建置」是預設目標。  
  
     **/v:d** 參數會指定建置流程的詳細描述。  
  
     此時應該顯示下列幾行：  
  
     **將略過目標 "Build"，因為所有輸出檔對於其輸入檔而言都已更新。**  
  
     **輸入檔：HelloWorld.cs**  
  
     **輸出檔：BinMSBuildSample.exe**  
  
     MSBuild 會略過「建置」目標，因為自上次建置應用程式以來，從未變更任何原始程式檔。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例顯示的專案檔會編譯 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 應用程式，並記錄包含輸出檔名稱的訊息。  
  
### <a name="code"></a>程式碼  
  
```csharp  
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
  
### <a name="comments"></a>註解  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例顯示的專案檔會編譯 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 應用程式，並記錄包含輸出檔名稱的訊息。  
  
### <a name="code"></a>程式碼  
  
```vb  
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
  
## <a name="whats-next"></a>後續步驟？  
 Visual Studio 可以自動執行本逐步解說中提及的大量工作。 若要了解如何使用 Visual Studio 建立、編輯、建置及測試 MSBuild 專案檔，請參閱[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。  
  
## <a name="see-also"></a>請參閱  
[MSBuild 概觀](msbuild.md)  
 [MSBuild 參考](../msbuild/msbuild-reference.md)
