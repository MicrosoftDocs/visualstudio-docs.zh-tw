---
title: 創建基本項目系統,第 1 部分 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739732"
---
# <a name="create-a-basic-project-system-part-1"></a>建立基本項目系統,第 1 部分
在 Visual Studio 中,專案是開發人員用來組織原始程式碼檔和其他資產的容器。 專案在**解決方案資源管理器**中顯示為解決方案的子級。 專案允許您組織、構建、除錯和部署原始碼,並創建對 Web 服務、資料庫和其他資源的參考。

 專案在專案檔中定義,例如 Visual C++ 專案的 *.csproj*檔。 您可以建立自己的項目類型,該類型具有自己的專案檔名副檔名。 有關項目類型的詳細資訊,請參考[項目類型](../extensibility/internals/project-types.md)。

> [!NOTE]
> 如果您需要使用自訂項目類型擴展 Visual Studio,我們強烈建議利用[Visual Studio 專案系統](https://github.com/Microsoft/VSProjectSystem)(VSPS),該系統比從頭開始建構專案系統具有許多優勢:
>
> - 更容易上船。  即使是基本的專案系統也需要數萬行代碼。  利用 VSPS 可將載入成本降低到幾下,然後再準備好根據您的需求進行自定義。
> - 更輕鬆的維護。  通過利用 VSPS,您只需要維護自己的方案。  我們處理所有專案系統基礎結構的維護。
>
>   如果您需要定位比 Visual Studio 2013 更老的 Visual Studio 版本,您將無法在 Visual Studio 擴充中利用 VSPS。  如果是這樣的話,這個演練是一個很好的開始的地方。

 本演練演示如何建立具有專案檔名*副檔名 .myproj*的項目類型。 本演練借用了現有的 Visual C++ 專案系統。

> [!NOTE]
> 有關延伸項目的更多範例,請參閱[VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

 本演練將介紹如何完成這些任務:

- 創建基本項目類型。

- 創建基本專案範本。

- 向可視化工作室註冊項目範本。

- 通過打開 **「新專案」** 對話方塊,然後使用範本創建專案實例。

- 為專案系統創建項目工廠。

- 為專案系統創建專案節點。

- 為專案系統添加自定義圖示。

- 實現基本範本參數替換。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

 您還必須下載[項目的託管包框架的](https://github.com/tunnelvisionlabs/MPFProj10)原始程式碼。 將檔案提取到要創建的解決方案可訪問的位置。

## <a name="create-a-basic-project-type"></a>建立基本項目型態
 創建名為 **「簡單專案」的**C# VSIX 專案。 (**檔案** > **新項目** > **Project**,然後**可視化 C#** > **可擴充性** > **VSIX 專案**)。 添加可視化工作室包專案範本(在**解決方案資源管理器**上,右鍵單擊專案節點並選擇 **'添加新** > **專案**",然後轉到 **"擴展可視化** > **工作室"包**)。 命名檔案*簡單專案套件*。

## <a name="creating-a-basic-project-template"></a>建立基本項目樣本
 現在,您可以修改此基本 VS 包以實現新的 *.myproj*專案類型。 要創建基於 *.myproj*專案類型的專案,Visual Studio 必須知道要添加到新專案的檔、資源和引用。 要提供此資訊,請將專案檔放在專案範本資料夾中。 當使用者使用 *.myproj*專案建立專案時,檔案將複製到新專案。

### <a name="to-create-a-basic-project-template"></a>建立基本項目樣本

1. 新增三個資料夾,另一個資料夾位於另一個資料夾下:*樣本的字目的項目的字目 。* (在**解決方案資源管理器**中,右鍵按**一下 「簡單專案專案**」,指向 **「添加**」,然後單擊 **「新建資料夾**」。 命名資料夾*樣本*。 在 *「樣本」* 資料夾中,添加名為 *「專案」的*資料夾。 在 *「專案」* 資料夾中,添加名為 *「簡單專案*」的資料夾。

2. 在*樣本\專案\簡單項目*資料夾中,添加一個位圖圖像檔,用作名為 *「簡單專案.ico」* 的圖示。 按下「**添加**」時,圖示編輯器將打開。

3. 使圖示與眾不同。 此圖示將顯示在演練後面的新**專案**對話框中。

    ![簡單專案圖示](../extensibility/media/simpleprojicon.png "簡單圖示")

4. 保存圖示並關閉圖示編輯器。

5. 在*樣本\專案\簡單項目*資料夾中,添加名為*Program.cs***的類**專案。

6. 將現有代碼替換為以下行。

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > 這不是Program.cs代碼的最終形式;但是,這不是*代碼*的最終形式。替換參數將在後面的步驟中處理。 您可能會看到編譯錯誤,但只要檔的**BuildAction**是**內容**,您應該能夠像往常一樣生成和運行專案。

7. 儲存檔案。

8. 將*AssemblyInfo.cs*檔案從 *「屬性*」 的資料夾複製到*項目。_簡單專案*資料夾。

9. 在 *「專案_簡單專案」* 資料夾中添加名為*SimpleProject.myproj*的 XML 檔。

   > [!NOTE]
   > 此類型的所有項目的檔案名副檔名是 *.myproj*。 如果要更改它,則必須在演練中提及的任何地方更改它。

10. 將現有內容替換為以下行。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. 儲存檔案。

12. **Include in VSIX**在 **「屬性」** 視窗中,將*AssemblyInfo.cs、Program.cs,**簡單專案. ico*和*SimpleProject.myproj*的**生成操作**設定為*Program.cs***"true"** **Content**

    此專案範本描述了具有調試配置和發佈配置的基本 Visual C++ 專案。 該專案包括兩個源檔 *,AssemblyInfo.cs**和Program.cs*,以及多個程式集引用。 從範本建立專案時,ProjectGuid 值將自動替換為新的 GUID。

    在**解決方案資源管理員**中,展開**的範本**資料夾應如下所示:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>建立基本項目工廠
 您必須告訴 Visual Studio 專案範本資料夾的位置。 為此,向實現項目工廠的 VSPackage 類添加一個屬性,以便在生成 VSPackage 時將範本位置寫入系統註冊表。 首先創建專案工廠 GUID 識別的基本項目工廠。 使用<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>屬性將項目工廠連線到`SimpleProjectPackage`類別 。

### <a name="to-create-a-basic-project-factory"></a>建立基本項目工廠

1. 為專案工廠創建 GUID(在 **"工具"** 選單上,按下"創建 GUID")或使用以下範例中的**GUID。** 將 GUID 添加`SimpleProjectPackage`到具有`PackageGuidString`已定義的節附近的類。 GUID 必須同時使用 GUID 形式和字串形式。 生成的代碼應類似於以下範例。

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. 將類添加到名為*SimpleProjectFactory.cs*的頂部*簡單項目*資料夾。

3. 加入以下 using 指示詞：

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. 向`SimpleProjectFactory`類添加 GUID 屬性。 屬性的值是新項目工廠 GUID。

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   現在,您可以註冊項目範本。

### <a name="to-register-the-project-template"></a>註冊項目範本

1. 在*SimpleProjectPackage.cs*SimpleProjectPackage.cs<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>中`SimpleProjectPackage`,向 類添加屬性,如下所示。

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. 重建解決方案並驗證其生成時是否沒有錯誤。

    重建註冊項目範本。

   參數`defaultProjectExtension``possibleProjectExtensions`並設置為專案檔名副檔名 *(.myproj*)。 參數`projectTemplatesDirectory`設定為*範本*資料夾的相對路徑。 在生成期間,此路徑將轉換為完整生成並添加到註冊表以註冊項目系統。

## <a name="test-the-template-registration"></a>測試樣本註冊
 樣本註冊告訴 Visual Studio 專案樣本資料夾的位置,以便 Visual Studio 可以在 **「新專案」** 對話框中顯示範本名稱和圖示。

### <a name="to-test-the-template-registration"></a>測試樣本註冊

1. 按**F5**開始調試 Visual Studio 的實驗實例。

2. 在實驗實例中,創建新創建的專案類型的新專案。 在 **"新項目"** 對話方塊中,應看到 **「已安裝範本**」下的 **「簡單專案**」。。

   現在,您有一個已註冊的項目工廠。 但是,它還不能創建專案。 專案包和專案工廠協同工作以創建和初始化專案。

## <a name="add-the-managed-package-framework-code"></a>新增託管套件框架代碼
 實現專案包和項目工廠之間的連接。

- 匯入託管包框架的原始程式碼檔。

    1. 卸載簡單項目專案(在**解決方案資源管理員**中,選擇專案節點,並在上下文菜單上單擊 **"卸載專案**"),並在 XML 編輯器中打開專案檔。

    2. 將以下塊添加到專案檔(略高於\<"導入>塊)。 在`ProjectBasePath`剛剛下載的託管包框架代碼中設置為*ProjectBase.file 檔案*的位置。 您可能需要向路徑名稱添加反斜杠。 如果不這樣做,專案可能無法找到託管包框架原始程式碼。

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > 不要忘記路徑末尾的斜杠。

    3. 重新載入專案。

    4. 加入下列組件的參考：

        - `Microsoft.VisualStudio.Designer.Interfaces`(在*\<VSSDK 中安裝>_VisualStudio整合的\公共_程式集\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>初始化項目工廠

1. 在*SimpleProjectPackage.cs*檔案中,`using`新增以下 指令。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. 從`Microsoft.VisualStudio.Package.ProjectPackage``SimpleProjectPackage`派生類。

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. 註冊項目工廠。 將以下行添加到`SimpleProjectPackage.Initialize`方法,只是`base.Initialize`在之後。

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. 實現抽象屬性`ProductUserContext`:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. 在*SimpleProjectFactory.cs*,在`using`現有`using`指令 之後添加以下指令。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. 從`ProjectFactory``SimpleProjectFactory`派生類。

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. 將以下虛擬方法添加到`SimpleProjectFactory`類。 您將在後面的一節中實現此方法。

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. 將以下欄位和建構函數添加到`SimpleProjectFactory`類。 此`SimpleProjectPackage`引用緩存在專用欄位中,以便可用於設置服務提供商網站。

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. 重建解決方案並驗證其生成時是否沒有錯誤。

## <a name="test-the-project-factory-implementation"></a>測試項目工廠實施
 測試是否調用專案工廠實現的構造函數。

### <a name="to-test-the-project-factory-implementation"></a>測試項目工廠實施

1. 在*SimpleProjectFactory.cs*檔中`SimpleProjectFactory`,在建構函數中的下一行設置斷點。

    ```csharp
    this.package = package;
    ```

2. 按**F5**啟動可視化工作室的實驗實例。

3. 在實驗實例中,開始創建新專案。 在 **"新項目**"對話框中,選擇 **「簡單項目**專案」類型,然後單擊「**確定**」。 執行會在中斷點停止。

4. 清除斷點並停止調試。 由於我們尚未創建專案節點,因此專案創建代碼仍引發異常。

## <a name="extend-the-projectnode-class"></a>延伸 ProjectNode 類別
 現在,您可以實現從`SimpleProjectNode`類派生`ProjectNode`的 類。 基`ProjectNode`類別處理以下項目建立工作:

- 將專案範本檔*SimpleProject.myproj 複製到*新專案資料夾。 根據在 **「新項目」** 對話方塊中輸入的名稱重新命名複本。 屬性`ProjectGuid`值替換為新的 GUID。

- 遍歷項目範本檔的 MSBuild 元素 *,SimpleProject.myproj*`Compile`,並查找 元素。 對於每個`Compile`目標檔,將檔案複製到新的項目資料夾。

  衍生`SimpleProjectNode`的類別處理以下工作:

- 啟用創建或選擇**解決方案資源管理員**中專案和檔案節點的圖示。

- 啟用指定其他項目範本參數替換。

### <a name="to-extend-the-projectnode-class"></a>延伸 ProjectNode 類別

1. 新增名為 `SimpleProjectNode.cs`的類別。

2. 將現有的程式碼取代為下列程式碼。

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   此類`SimpleProjectNode`實現具有以下重寫方法:

- `ProjectGuid`返回專案工廠 GUID。

- `ProjectType`返回項目類型的本地化名稱。

- `AddFileFromTemplate`將選取檔案從樣本資料夾複製到目標專案。 此方法在後面的一節中進一步實現。

  建構`SimpleProjectNode`函數`SimpleProjectFactory`與 建構函`SimpleProjectPackage`數一樣,在私有欄位中緩存引用,以便以後使用。

  要將`SimpleProjectFactory`類連接到類`SimpleProjectNode`,`SimpleProjectNode``SimpleProjectFactory.CreateProject`必須在方法中實例化新,並將其緩存在私有欄位中,以便以後使用。

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>連接項目工廠類別和節點類別

1. 在*SimpleProjectFactory.cs*檔中,`using`新增以下 指令:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. 使用以下`SimpleProjectFactory.CreateProject`代碼替換方法。

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. 重建解決方案並驗證其生成時是否沒有錯誤。

## <a name="test-the-projectnode-class"></a>測試 ProjectNode 類別
 測試專案工廠以查看它是否創建了專案層次結構。

### <a name="to-test-the-projectnode-class"></a>測試 ProjectNode 類別

1. 按 **F5** 開始偵錯。 在實驗實例中,創建新的簡單專案。

2. Visual Studio 應調用專案工廠以創建專案。

3. 關閉 Visual Studio 的實驗執行個體。

## <a name="add-a-custom-project-node-icon"></a>新增自訂項目節點圖示
 前面部分中的項目節點圖示是預設圖示。 您可以將其更改為自訂圖示。

### <a name="to-add-a-custom-project-node-icon"></a>新增自訂項目節點圖示

1. 在 **「資源」** 資料夾中,添加名為*SimpleProjectNode.bmp*的位圖檔。

2. 在 **「屬性」** 視窗中,將位圖減小到 16 x 16 圖元。 使位圖與眾不同。

    ![簡單專案 Comm](../extensibility/media/simpleprojprojectcomm.png "簡單專業專案通訊")

3. 在 **「屬性」** 視窗中,將位圖的**生成操作**更改為 **「嵌入資源**」 。

4. 在*SimpleProjectNode.cs*中`using`,新增以下指令:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. 將以下靜態欄位和建構函數添加到`SimpleProjectNode`類。

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. 將以下屬性添加到類的`SimpleProjectNode`開頭。

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. 將實例構造函數替換為以下代碼。

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   在靜態構造期間`SimpleProjectNode`,從程式集清單資源檢索專案節點位圖,並將其緩存在專用欄位中,以便以後使用。 請注意圖像路徑的<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>語法。 要檢視嵌入在程式集中的清單資源的名稱,請使用方法<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>。 將此方法應用於程式集時`SimpleProject`,結果應如下所示:

- *簡單專案.資源.資源*

- *視覺化工作室.專案資源*

- *簡單專案.VS包.資源*

- *資源.影像.bmp*

- *微軟.VisualStudio.專案.不要再次顯示對話.資源*

- *微軟.VisualStudio.專案.安全警告對話.資源*

- *簡單專案.資源.簡單專案節點.bmp*

  在實例建構期間,`ProjectNode`基類載入*Resources.imagelis.bmp*,其中嵌入了資源 *_imagelis.bmp*中常用的 16 x 16 位元圖。 此點陣圖清單可`SimpleProjectNode`供`ImageHandler.ImageList`作為 。 `SimpleProjectNode`將專案節點點陣圖追加到清單中。 圖像清單中的項目節點位圖的偏移量將緩存,供以後用作公共`ImageIndex`屬性的值。 Visual Studio 使用此屬性來確定要顯示為專案節點圖示的點陣圖。

## <a name="test-the-custom-project-node-icon"></a>測試自訂項目節點圖示
 測試專案工廠以查看它是否創建具有自定義專案節點圖示的專案層次結構。

### <a name="to-test-the-custom-project-node-icon"></a>測試自訂項目節點圖示

1. 開始調試,並在實驗實例中創建新的 SimpleProject。

2. 在新創建的專案中,請注意*SimpleProjectNode.bmp*用作專案節點圖示。

     ![簡單專案新增專案節點](../extensibility/media/simpleprojnewprojectnode.png "簡單專業專案節點")

3. 在程式碼編輯器中開啟 *Program.cs*。 您應該會看到類似於以下代碼的原始程式碼。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     請注意,範本參數$nameSpace$和 $className$沒有新值。 您將在下一節中瞭解如何實現範本參數替換。

## <a name="substitute-template-parameters"></a>取代樣本參數
 在前面的一節中,您可以使用`ProvideProjectFactory`屬性向 Visual Studio 註冊項目範本。 以這種方式註冊範本資料夾的路徑,可以通過重寫和`ProjectNode.AddFileFromTemplate`擴展 類來啟用基本的範本參數替換。 有關詳細資訊,請參閱[新專案生成:在引擎蓋下,第二部分](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 現在向`AddFileFromTemplate`類添加替換代碼。

### <a name="to-substitute-template-parameters"></a>取代樣本參數

1. 在*SimpleProjectNode.cs*檔案中,`using`新增以下指令。

   ```csharp
   using System.IO;
   ```

2. 使用以下`AddFileFromTemplate`代碼替換方法。

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. 在`className`賦值語句之後,在方法中設置斷點。

   賦值語句確定命名空間和新類名稱的合理值。 使用這些新`ProjectNode.FileTemplateProcessor.AddReplace`值,兩個方法調用替換相應的範本參數值。

## <a name="test-the-template-parameter-substitution"></a>測試樣本參數取代
 現在,您可以測試範本參數替換。

### <a name="to-test-the-template-parameter-substitution"></a>測試樣本參數取代

1. 開始調試,並在實驗實例中創建新的 SimpleProject。

2. 執行停止在`AddFileFromTemplate`方法的斷點處。

3. 檢查`nameSpace``className`和 參數的值。

   - `nameSpace`在\<*[樣本\專案]簡單專案_簡單專案.myproj*專案範本檔中給出 rootNamespace> 元素的值。 此處的值為 `MyRootNamespace`。

   - `className`給定類源檔名的值,而不提供檔名擴展名。 在這種情況下,要複製到目標資料夾的第一個檔案*AssemblyInfo.cs*。因此,類別名稱的值為`AssemblyInfo`。

4. 刪除斷點,然後按**F5**繼續執行。

    可視化工作室應完成項目創建。

5. 在程式碼編輯器中開啟 *Program.cs*。 您應該會看到類似於以下代碼的原始程式碼。

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    請注意,命名空間現在是`MyRootNamespace`,類名稱現在是`Program`。

6. 開始進行專案偵錯。 新項目應編譯、運行並顯示"您好 VSX !!!" 。

    ![簡單專案命令](../extensibility/media/simpleprojcommand.png "簡單專業命令")

   恭喜！ 您已經實現了基本的託管項目系統。
