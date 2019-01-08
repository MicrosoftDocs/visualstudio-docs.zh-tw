---
title: 逐步解說：使用 MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 12/18/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13493b9ab21386ff5856fd6046e963d362071570
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648916"
---
# <a name="walkthrough-use-msbuild"></a>逐步解說：使用 MSBuild
MSBuild 是 Microsoft 和 Visual Studio 的建置平台。 此逐步解說將介紹 MSBuild 的建置區塊，以及示範如何撰寫和管理 MSBuild 專案及進行偵錯。 學習內容：

-   建立和管理專案檔。

-   如何使用組建屬性

-   如何使用組建項目。

您可以從 Visual Studio 或**命令視窗**執行 MSBuild。 在本逐步解說中，您將使用 Visual Studio 來建立 MSBuild 專案檔。 您可以在 Visual Studio 中編輯專案檔，然後使用**命令視窗**建置專案並檢查結果。

## <a name="create-an-msbuild-project"></a>建立 MSBuild 專案
 Visual Studio 專案系統是以 MSBuild 為基礎。 這可讓您輕鬆地使用 Visual Studio 建立新的專案檔。 在本節中，您將建立 Visual C# 專案檔。 您可以選擇改為建立 Visual Basic 專案檔。 在本逐步解說的內容中，這兩個專案檔之間的差異非常小。

#### <a name="to-create-a-project-file"></a>建立專案檔

1.  開啟 Visual Studio。

2.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

3.  在 [新增專案] 對話方塊中，選取 [Visual C#] 專案類型，然後選取 [Windows Forms 應用程式] 範本。 在 [名稱]  方塊中，輸入 `BuildApp`。 輸入方案的 [位置]，例如 *D:\\*。 接受 [為方案建立目錄] (已選取)、[加入至原始檔控制] (未選取) 及 [方案名稱] (**BuildApp**) 的預設值。

4.    按一下 [確定] 以建立專案檔。

## <a name="examine-the-project-file"></a>檢查專案檔
 在上一節中，您使用了 Visual Studio 來建立 Visual C# 專案檔。 專案檔會在 [方案總管] 中，透過名為 BuildApp 的專案節點來顯示。 您可以使用 Visual Studio 程式碼編輯器來檢查專案檔。

#### <a name="to-examine-the-project-file"></a>檢查專案檔

1.  在 [方案總管] 中，按一下專案節點 **BuildApp**。

2.  在 [屬性] 瀏覽器中，請注意 [專案檔] 屬性為 *BuildApp.csproj*。 所有專案檔名稱的尾碼都是 *proj*。 如果您已建立 Visual Basic 專案，則專案檔名稱會是 *BuildApp.vbproj*。

3.  以滑鼠右鍵按一下專案節點，然後按一下 [卸載專案]。

4.  再次以滑鼠右鍵按一下專案節點，然後按一下 [編輯 BuildApp.csproj]。

     該專案檔隨即出現在程式碼編輯器中。

## <a name="targets-and-tasks"></a>目標和工作
專案檔是含有根節點 [Project](../msbuild/project-element-msbuild.md) 的 XML 格式檔案。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

您必須在 Project 項目中指定 xmlns 命名空間。 若新專案中存在 `ToolsVersion`，其必須為 "15.0"。

建置應用程式的工作是利用 [Target](../msbuild/target-element-msbuild.md) 和 [Task](../msbuild/task-element-msbuild.md) 項目來完成。

-   工作 (Task) 是工作 (Work) 的最小單位，也就是組建的「元素」。 工作是獨立的可執行檔元件，其中可能會有輸入和輸出。 專案檔中沒有任何目前參考或定義的工作。 您會在下列各節中將工作加入至專案檔。 如需詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md) 主題。

-   目標是一連串具名的工作。 如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)主題。

預設目標並未在專案檔中定義。 而是在匯入的專案中指定。 [Import](../msbuild/import-element-msbuild.md) 元素會指定匯入的專案。 例如，在 C# 專案中，預設目標會從檔案 *Microsoft.CSharp.targets* 匯入。

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

只要參考到它們，就能有效地將匯入的檔案插入至專案檔。

> [!NOTE]
> .NET Core 等部分專案類型會使用具 `Sdk` 屬性而非 `ToolsVersion` 屬性的簡化結構描述。 這些專案均具有隱含的匯入與不同的預設屬性值。

MSBuild 會持續追蹤組建的目標，並保證每個目標的建置不會超過一次。

## <a name="add-a-target-and-a-task"></a>加入目標和工作
 將目標加入至專案檔。 將工作加入至會印出訊息的目標。

#### <a name="to-add-a-target-and-a-task"></a>加入目標和工作

1.  將下列這幾行加入至專案檔，緊接在 Import 陳述式之後：

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

     這會建立名為 HelloWorld 的目標。 請注意，您在編輯專案檔時必須具備 IntelliSense 支援。

2.  將這幾行加入至 HelloWorld 目標，因此，產生的區段會看起來如下：

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3.  儲存專案檔。

Message 工作是 MSBuild 隨附的許多工作之一。 如需可用工作的完整清單和用法資訊，請參閱[工作參考](../msbuild/msbuild-task-reference.md)。

Message 工作會取得 Text 屬性的字串值做為輸入，並顯示於輸出裝置上。 HelloWorld 目標會執行 Message 工作兩次：第一次顯示 "Hello"，接著顯示 "World"。

## <a name="build-the-target"></a>建置目標
 從 Visual Studio 的 [開發人員命令提示字元] 執行 MSBuild，以建置前述內容所定義的 HelloWorld 目標。 使用 -target 或 -t 命令列參數選取目標。

> [!NOTE]
>  我們會在下列各節中，將**開發人員命令提示字元**稱為**命令視窗**。

#### <a name="to-build-the-target"></a>建置目標

1. 開啟 [命令視窗]。

   (Windows 10) 在工作列的搜尋方塊中開始鍵入工具名稱，例如 `dev` 或 `developer command prompt`。 這會顯示符合搜尋模式的已安裝應用程式清單。

   如果您需要以手動方式尋找，檔案是 *LaunchDevCmd.bat*，位於 <visualstudio installation folder>\<版本>\Common7\Tools 資料夾。

2. 從命令視窗，瀏覽至包含專案檔的資料夾，在此案例中為 *D:\BuildApp\BuildApp*。

3. 使用命令參數 -t:HelloWorld 執行 msbuild。 這會選取並建置 HelloWorld 目標：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. 檢查 [命令視窗] 中的輸出。 您應該會看到 "Hello" 和 "World" 這兩行：

    ```
    Hello
    World
    ```

> [!NOTE]
>  如果您看到了 `The target "HelloWorld" does not exist in the project`，則您可能忘了在程式碼編輯器中儲存該專案檔。 請儲存檔案，然後再試一次。

 藉由交替使用程式碼編輯器和命令視窗，您可以變更專案檔，並快速查看結果。

## <a name="build-properties"></a>組建屬性
 組建屬性是會引導組建的名稱/值組。 專案檔頂端已經定義了數個組建屬性：

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 所有屬性都是 PropertyGroup 項目的子項目。 屬性的名稱是子項目的名稱，而屬性的值是子項目的文字項目。 例如，套用至物件的

```xml
<TargetFrameworkVersion>v15.0</TargetFrameworkVersion>
```

 會定義名為 TargetFrameworkVersion 的屬性，並賦予其字串值 "v15.0"。

 您隨時都能重新定義組建屬性。 如果

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 稍後出現在專案檔中，或在稍後會於專案檔中匯入的檔案中，則 TargetFrameworkVersion 會採用新值 "v3.5"。

## <a name="examine-a-property-value"></a>檢查屬性值
 若要取得屬性的值，請使用下列語法，其中 PropertyName 是屬性的名稱：

```xml
$(PropertyName)
```

 使用此語法來檢查專案檔中的某些屬性。

#### <a name="to-examine-a-property-value"></a>檢查屬性值

1.  從程式碼編輯器，使用此程式碼來取代 HelloWorld 目標：

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

2.  儲存專案檔。

3.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  檢查輸出結果， 您應該會看到這兩行 (您的 .NET Framework 版本可能不一樣)：

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

> [!NOTE]
>  如果您未看見這幾行，則您可能忘了在程式碼編輯器中儲存該專案檔。 請儲存檔案，然後再試一次。

### <a name="conditional-properties"></a>條件式屬性
 有條件地定義許多屬性 (例如 Configuration)，也就是 Condition 屬性會出現在屬性項目中。 只有當條件評估為 "true" 時，才能定義或重新定義條件式屬性。 請注意，未定義屬性的預設值是空字串。 例如，套用至物件的

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 表示「如果尚未定義 Configuration 屬性，請加以定義，並提供值 'Debug'」。

 幾乎所有的 MSBuild 項目都會有一個 Condition 屬性。 如需使用 Condition 屬性的詳細討論，請參閱[條件](../msbuild/msbuild-conditions.md)。

### <a name="reserved-properties"></a>保留的屬性
 MSBuild 保留一些屬性名稱來儲存專案檔和 MSBuild 二進位檔案的相關資訊。 MSBuildToolsPath 是保留的屬性範例。 保留的屬性是使用 $ 標記法來參考，如同任何其他屬性。 如需詳細資訊，請參閱[＜How to：參考專案檔的名稱或位置](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)和 [MSBuild 保留和已知的屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)。

### <a name="environment-variables"></a>環境變數
 您可以使用和組建屬性一樣的方式，來參考專案檔中的環境變數。 例如，若要在專案檔中使用 PATH 環境變數，請使用 $(Path)。 如果專案包含與環境變數相同名稱的專案定義，則專案中的屬性會覆寫環境變數的值。 如需詳細資訊，請參閱[＜How to：在組建中使用環境變數](../msbuild/how-to-use-environment-variables-in-a-build.md)。

## <a name="set-properties-from-the-command-line"></a>從命令列設定屬性
 您可以在命令列上，使用 -property 或 -p 命令列參數定義屬性。 接收自命令列的屬性值會覆寫專案檔和環境變數中所設定的屬性值。

#### <a name="to-set-a-property-value-from-the-command-line"></a>從命令列設定專案值

1.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

2.  檢查輸出結果， 您應該會看到下列這一行：

    ```
    Configuration is Release.
    ```

MSBuild 會建立 Configuration 屬性，並提供值 "Release"。

## <a name="special-characters"></a>特殊字元
 在 MSBuild 專案檔中，有某些字元具有特殊意義。 這些字元範例包括分號 (;) 和星號 (*)。 若要使用這些特殊字元作為專案檔中的常值，就必須使用 %\<xx> 語法來指定它們，其中 \<xx> 代表字元的 ASCII 十六進位值。

 變更 Message 工作以顯示具有特殊字元的 Configuration 屬性值，讓它更容易閱讀。

#### <a name="to-use-special-characters-in-the-message-task"></a>在 Message 工作中使用特殊字元

1.  從程式碼編輯器，使用下列這一行來取代這兩個 Message 工作：

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

2.  儲存專案檔。

3.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  檢查輸出結果， 您應該會看到下列這一行：

    ```
    $(Configuration) is "Debug"
    ```

如需詳細資訊，請參閱 [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md)。

## <a name="build-items"></a>組建項目
 項目是一種資訊，通常是檔案名稱，可用來做為建置系統的輸入。 例如，可能會將代表原始程式檔的項目集合傳遞至名為 Compile 的工作，以便將它們編譯為組件。

 所有項目 (Item) 都是 ItemGroup 項目 (Element) 的子項目 (Element)。 項目 (Item) 名稱是子項目 (Element) 的名稱，而項目 (Item) 值是子項目 (Element) 的 Include 屬性值。 系統會將名稱相同的項目值收集到該名稱的項目類型。  例如，套用至物件的

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 定義一個包含兩個項目的項目群組。 Compile 項目類型有兩個值：*Program.cs* 和 *Properties\AssemblyInfo.cs*。

 下列程式碼會在一個 Include 屬性中宣告這兩個檔案 (以分號分隔)，藉以建立相同的項目類型。

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

> [!NOTE]
>  檔案路徑會相對於包含 MSBuild 專案檔的資料夾。

## <a name="examine-item-type-values"></a>檢查項目類型值
 若要取得項目類型的值，請使用下列語法，其中 ItemType 為項目類型的名稱：

```xml
@(ItemType)
```

 使用此語法來檢查專案檔中的 Compile 項目類型。

#### <a name="to-examine-item-type-values"></a>檢查項目類型值

1.  從程式碼編輯器，使用下列程式碼來取代 HelloWorld 目標工作：

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

2.  儲存專案檔。

3.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  檢查輸出結果， 您應該會看到下列這一長串的內容：

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

預設會以分號分隔項目類型的值。

若要變更項目類型的分隔符號，請使用下列語法，其中 ItemType 是項目類型，而 Separator 是一或多個分隔字元的字串：

```xml
@(ItemType, Separator)
```

變更 Message 工作來使用歸位字元和換行字元 (%0A%0D)，以便每行顯示一個 Compile 項目。

#### <a name="to-display-item-type-values-one-per-line"></a>每行顯示一個項目類型值

1.  從程式碼編輯器，使用下列這一行來取代 Message 工作：

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2.  儲存專案檔。

3.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  檢查輸出結果， 您應該會看到下列這幾行：

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Include、Exclude 和萬用字元
 您可以使用萬用字元 "*"、"\*\*" 及 "?" 搭配 Include 屬性，來將項目加入至項目類型。 例如，套用至物件的

```xml
<Photos Include="images\*.jpeg" />
```

 將 *images* 資料夾中所有副檔名為 *.jpeg* 的檔案加入至 Photos 項目類型，同時

```xml
<Photos Include="images\**.jpeg" />
```

 將 *images* 資料夾及其所有子資料夾中所有副檔名為 *.jpeg* 的檔案加入至 Photos 項目類型。 如需更多範例，請參閱[如何：選取要建置的檔案](../msbuild/how-to-select-the-files-to-build.md)。

 請注意，宣告項目時，會將它們加入至項目類型。 例如，套用至物件的

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 建立名為 Photo 的項目類型，其中包含 *image* 資料夾中副檔名為 *.jpeg* 或 *.gif* 的所有檔案。 這就相當於下列這一行：

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 您可以使用 Exclude 屬性，從項目類型中排除項目。 例如，套用至物件的

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 將副檔名為 *.cs* 的所有檔案加入至 Compile 項目類型，但名稱包含 *Designer* 字串的檔案除外。 如需更多範例，請參閱[如何：從組建中排除檔案](../msbuild/how-to-exclude-files-from-the-build.md)。

Exclude 屬性只會影響包含這兩者之 Item 項目 (Element) 中由 Include 屬性所加入的項目 (Item)。 例如，套用至物件的

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

不會排除 *Form1.cs* 檔，這是在前一個 Item 項目中加入的檔案。

##### <a name="to-include-and-exclude-items"></a>包含與排除項目

1.  從程式碼編輯器，使用下列這一行來取代 Message 工作：

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2.  加入這個項目 (Item) 群組，緊接在 Import 項目 (Element) 之後：

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3.  儲存專案檔。

4.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5.  檢查輸出結果， 您應該會看到下列這一行：

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>項目中繼資料
 除了 Include 和 Exclude 屬性所收集的資訊之外，項目可能還會包含中繼資料。 若工作需要更多關於項目的資訊 (而不只是項目值)，就能使用此中繼資料。

 在專案檔中宣告項目 (Item) 中繼資料的方式，就是建立一個具有中繼資料名稱的項目 (Element)，做為項目 (Item) 的子項目 (Element)。 項目可以有零或多個中繼資料值。 例如，下列 CSFile 項目具有值為 "Fr" 的 Culture 中繼資料：

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 若要取得項目類型的中繼資料值，請使用下列語法，其中 ItemType 是項目類型的名稱，而 MetaDataName 是中繼資料的名稱：

```xml
%(ItemType.MetaDataName)
```

#### <a name="to-examine-item-metadata"></a>檢查項目中繼資料

1.  從程式碼編輯器，使用下列這一行來取代 Message 工作：

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2.  儲存專案檔。

3.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  檢查輸出結果， 您應該會看到下列這幾行：

    ```
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

請注意 "Compile.DependentUpon" 一詞多次出現的方式。 在目標內搭配此語法使用中繼資料，會導致「批次處理」。 批次處理表示會針對每個唯一的中繼資料值執行一次目標內的工作。 這是相當於「for 迴圈」的一般程式設計建構的 MSBuild 指令碼。 如需詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。

### <a name="well-known-metadata"></a>已知的中繼資料
 每次將項目加入至項目清單時，即會為該項目指派一些已知的中繼資料。 例如，%(Filename) 會傳回任何項目的檔案名稱。 如需已知中繼資料的完整清單，請參閱[已知的項目中繼資料](../msbuild/msbuild-well-known-item-metadata.md)。

##### <a name="to-examine-well-known-metadata"></a>檢查已知的中繼資料

1.  從程式碼編輯器，使用下列這一行來取代 Message 工作：

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2.  儲存專案檔。

3.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  檢查輸出結果， 您應該會看到下列這幾行：

    ```
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

藉由比較上述兩個範例，您會發現，儘管 Compile 項目類型中不是每個項目都具有 DependentUpon 中繼資料，但所有項目都具有已知的 Filename 中繼資料。

### <a name="metadata-transformations"></a>中繼資料轉換
 項目清單可以轉換為新的項目清單。 若要轉換項目清單，請使用下列語法，其中 \<ItemType> 是項目類型的名稱，而 \<MetadataName> 是中繼資料的名稱：

```xml
@(ItemType -> '%(MetadataName)')
```

例如，您可以使用像是 `@(SourceFiles -> '%(Filename).obj')` 的運算式，將原始程式檔的項目清單轉換為目的檔集合。 如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。

##### <a name="to-transform-items-using-metadata"></a>使用中繼資料轉換項目

1.  從程式碼編輯器，使用下列這一行來取代 Message 工作：

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2.  儲存專案檔。

3.  從 [命令視窗]，輸入並執行這一行：

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  檢查輸出結果， 您應該會看到下列這一行：

    ```
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

請注意，此語法中所表示的中繼資料不會導致批次處理。

## <a name="whats-next"></a>後續步驟
 若要了解如何逐步建立簡單的專案檔，請嘗試[逐步解說︰從頭建立 MSBuild 專案檔案](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)。

## <a name="see-also"></a>另請參閱

- [MSBuild 概觀](../msbuild/msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
