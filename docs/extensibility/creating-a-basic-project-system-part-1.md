---
title: 建立基本的專案系統，第 1 部分 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9fd695c5a33ea8ea7bb9895d34995abd37db7019
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843957"
---
# <a name="create-a-basic-project-system-part-1"></a>建立基本專案系統，第 1 部分
在 Visual Studio 中，專案會是開發人員用來組織原始程式碼檔和其他資產的容器。 專案會顯示為子系中的解決方案**方案總管 中**。 專案可讓您組織、 建置、 偵錯和部署來源的程式碼及建立 Web 服務、 資料庫和其他資源的參考。

 專案檔案中定義的專案，例如 *.csproj* Visual C# 專案檔。 您可以建立您自己副檔名自己專案的專案類型。 如需專案類型的詳細資訊，請參閱[專案類型](../extensibility/internals/project-types.md)。

> [!NOTE]
>  如果您需要使用自訂專案類型擴充 Visual Studio，我們強烈建議運用[Visual Studio 專案系統](https://github.com/Microsoft/VSProjectSystem)(VSP) 具有許多透過建置全新的專案系統的優點：
>
> - 更輕鬆入門訓練。  即使基本的專案系統需要數以萬計的幾行程式碼。  利用 VSP 降低上架成本來按幾下之前您已準備好您的需求加以自訂。
> - 更容易維護。  利用 VSP，您只需要維護您自己的案例。  我們會處理所有的專案系統基礎結構的保養。
>
>   如果您需要以早於 Visual Studio 2013 的 Visual Studio 的版本為目標，您將無法運用 VSP 在 Visual Studio 擴充功能。  如果是這樣，本逐步解說會是不錯的起點開始。

 本逐步解說會示範如何建立具有專案副檔名的專案類型 *.myproj*。 本逐步解說會藉助現有的 Visual C# 專案系統。

> [!NOTE]
>  如需擴充功能專案的範例，請參閱[VSSDK 範例](https://aka.ms/vs2015sdksamples)。

 本逐步解說將說明如何完成這些工作：

-   建立基本專案類型。

-   建立基本專案範本。

-   向 Visual Studio 專案範本。

-   建立專案執行個體 %installationdirectory**新的專案**] 對話方塊中，然後使用 [您的範本。

-   建立您的專案系統的專案處理站。

-   建立您的專案系統的專案節點。

-   加入專案系統的自訂圖示。

-   實作基本的範本參數替代。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

 您也必須下載的原始程式碼[專案的 Managed Package Framework](https://github.com/tunnelvisionlabs/MPFProj10)。 將檔案解壓縮至您要建立此解決方案可存取的位置。

## <a name="create-a-basic-project-type"></a>建立基本專案類型
 建立名為 C# VSIX 專案**SimpleProject**。 (**檔案** > **新** > **專案**，然後**Visual C#**  >  **擴充性** > **VSIX 專案**)。 加入 Visual Studio Package 專案項目範本 (在**方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** > **新項目**，然後移至**擴充性** > **Visual Studio 套件**)。 將檔案命名*SimpleProjectPackage*。

## <a name="creating-a-basic-project-template"></a>建立基本的專案範本
 現在，您可以修改此基本的 VSPackage 實作的新 *.myproj*專案類型。 若要建立的專案，根據 *.myproj*專案類型，Visual Studio 必須先知道哪些檔案、 資源和參考新增至新的專案。 為了提供這項資訊，請將專案檔中的專案範本資料夾。 當使用者使用 *.myproj*專案建立專案中，檔案會複製到新的專案。

### <a name="to-create-a-basic-project-template"></a>若要建立基本專案範本

1. 加入專案，其中一個 [其他] 中的三個資料夾：*Templates\Projects\SimpleProject*. (在**方案總管**，以滑鼠右鍵按一下**SimpleProject**專案節點，指向**新增**，然後按一下 **新資料夾**。 將資料夾命名*範本*。 在 *範本*資料夾中，新增名為的資料夾*專案*。 在*專案*資料夾中，新增名為的資料夾*SimpleProject*。)

2. 在  *Templates\Projects\SimpleProject*資料夾中，新增的點陣圖影像檔案，作為名為圖示*SimpleProject.ico*。 當您按一下 **新增**，圖示編輯器隨即開啟。

3. 確保特殊的圖示。 此圖示會出現在**新的專案**稍後在本逐步解說中的對話方塊。

    ![簡單專案圖示](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. 儲存圖示並關閉圖示編輯器。

5. 在  *Templates\Projects\SimpleProject*資料夾中，新增**類別**項目的名稱*Program.cs*。

6. 下列幾行取代現有的程式碼。

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
   >  這不是最終形式*Program.cs*程式碼，取代參數會在稍後步驟中處理。 您可能會看到編譯錯誤，但只要檔案**建置動作**是**內容**，您應該能夠建置並如往常般執行專案。

7. 儲存檔案。

8. 複製*AssemblyInfo.cs*檔案*屬性*資料夾*Projects\SimpleProject*資料夾。

9. 在  *Projects\SimpleProject*資料夾新增名為 XML 檔案*SimpleProject.myproj*。

   > [!NOTE]
   >  此類型的所有專案的都副檔名 *.myproj*。 如果您想要變更它，您必須變更它被提及的逐步解說中的每個地方。

10. 下列幾行取代現有的內容。

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

12. 在 **屬性**視窗中，將**建置動作**的*AssemblyInfo.cs*， *Program.cs*， *SimpleProject.ico*，並*SimpleProject.myproj*要**內容**，並設定其**Include in VSIX**屬性，以**True**.

    這個專案範本描述基本 Visual C# 專案的偵錯組態和發行組態。 專案包含兩個原始程式檔*AssemblyInfo.cs*並*Program.cs*，和數個組件參考。 從範本建立專案時，都會自動 ProjectGuid 值取代新的 GUID。

    在 **方案總管**，展開**範本**資料夾應該會出現，如下所示：

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>建立基本專案處理站
 您必須告訴 Visual Studio 專案範本資料夾的位置。 若要這樣做，請將屬性加入 VSPackage 類別實作 project factory，以便建置 VSPackage 時，將會寫入至系統登錄的範本位置。 開始建立專案的 factory GUID 所識別的基本專案處理站。 使用<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>屬性，以連接到 project factory`SimpleProjectPackage`類別。

### <a name="to-create-a-basic-project-factory"></a>若要建立基本專案 factory

1. 您專案的處理站建立 Guid (在**工具**功能表上，按一下**建立 GUID**)，或使用下列範例中的一個。 新增 Guid`SimpleProjectPackage`附近的區段已定義的類別`PackageGuidString`。 GUID 格式和字串格式必須是 Guid。 產生的程式碼應該類似下列的範例。

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. 將類別加入頂端*SimpleProject*名為資料夾*SimpleProjectFactory.cs*。

3. 新增下列 using 陳述式：

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. GUID 將屬性新增至`SimpleProjectFactory`類別。 屬性的值是新的 project factory 的 GUID。

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   現在您可以註冊您的專案範本。

### <a name="to-register-the-project-template"></a>若要註冊的專案範本

1. 在  *SimpleProjectPackage.cs*，新增<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>屬性設定為`SimpleProjectPackage`類別，如下所示。

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. 重建方案，並確認它建置無誤。

    重建登錄的專案範本。

   參數`defaultProjectExtension`並`possibleProjectExtensions`會設定為專案的副檔名 (*.myproj*)。 `projectTemplatesDirectory`參數設為相對路徑*範本*資料夾。 組建，這個路徑可以轉換成完整建置，且新增至註冊專案系統登錄。

## <a name="test-the-template-registration"></a>測試範本註冊
 範本註冊會告知 Visual Studio 專案範本資料夾的位置，讓 Visual Studio 可以顯示的範本名稱和圖示**新的專案** 對話方塊。

### <a name="to-test-the-template-registration"></a>若要測試範本註冊

1. 按下**F5**開始偵錯 Visual Studio 的實驗執行個體。

2. 在實驗執行個體中，建立您的新建立的專案類型的新專案。 在 [**新的專案**] 對話方塊中，您應該會看到**SimpleProject**之下**已安裝的範本**。

   現在您已註冊的專案處理站。 不過，它還無法建立專案。 專案封裝和專案的處理站一起建立和初始化專案。

## <a name="add-the-managed-package-framework-code"></a>加入 Managed Package Framework 中的程式碼
 實作專案套件與 project factory 之間的連線。

-   Managed Package Framework 中，匯入的原始程式碼檔案。

    1.  卸載 SimpleProject 專案 (在**方案總管**，選取專案節點，然後在操作功能表上按一下 **卸載專案**。) 和 XML 編輯器中開啟專案檔案。

    2.  將下列區塊新增至專案檔 (正上方\<匯入 > 區塊)。 設定`ProjectBasePath`的位置*ProjectBase.files*在 Managed Package Framework 程式碼中您剛才下載的檔案。 您可能必須新增反斜線的路徑名稱。 如果您不這樣做，專案可能無法找到的 Managed 封裝架構原始程式碼。

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        >  別忘了在路徑結尾的反斜線。

    3.  重新載入專案。

    4.  加入下列組件的參考：

        -   `Microsoft.VisualStudio.Designer.Interfaces` (in *\<VSSDK install>\VisualStudioIntegration\Common\Assemblies\v2.0*)

        -   `WindowsBase`

        -   `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>若要初始化 project factory

1.  在  *SimpleProjectPackage.cs*檔案中，新增下列`using`陳述式。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2.  衍生`SimpleProjectPackage`類別從`Microsoft.VisualStudio.Package.ProjectPackage`。

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3.  註冊專案 factory。 加入下列這一行加入`SimpleProjectPackage.Initialize`方法，正後方`base.Initialize`。

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4.  實作抽象屬性`ProductUserContext`:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5.  在  *SimpleProjectFactory.cs*，新增下列`using`陳述式的現有`using`陳述式。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6.  衍生`SimpleProjectFactory`類別從`ProjectFactory`。

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7.  新增下列虛擬方法，以`SimpleProjectFactory`類別。 您會實作這個方法，在稍後的章節。

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8.  加入下列欄位和建構函式以`SimpleProjectFactory`類別。 這`SimpleProjectPackage`參考快取中的私用欄位，讓它可以用於設定服務提供者站台。

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. 重建方案，並確認它建置無誤。

## <a name="test-the-project-factory-implementation"></a>測試 project factory 實作
 測試是否會呼叫您 project factory 實作的建構函式。

### <a name="to-test-the-project-factory-implementation"></a>若要測試的 project factory 實作

1.  在  *SimpleProjectFactory.cs*檔案中，在下一行中設定中斷點`SimpleProjectFactory`建構函式。

    ```csharp
    this.package = package;
    ```

2.  按下**F5**啟動 Visual Studio 的實驗執行個體。

3.  在實驗執行個體中，開始建立新的專案。 在 **新的專案**對話方塊中，選取**SimpleProject**專案類型，然後按一下**確定**。 執行會在中斷點停止。

4.  清除中斷點，然後停止偵錯。 因為我們有尚未建立的專案節點，則專案建立程式碼還是擲回例外狀況。

## <a name="extend-the-projectnode-class"></a>擴充 ProjectNode 類別
 現在您可以實作`SimpleProjectNode`類別，衍生自`ProjectNode`類別。 `ProjectNode`基底類別處理的專案建立下列工作：

- 將專案的範本檔案，複製*SimpleProject.myproj*，新的專案資料夾。 複本會根據輸入中的名稱重新命名**新的專案** 對話方塊。 `ProjectGuid`屬性值會取代新的 GUID。

- 周遊的專案範本檔案的 MSBuild 項目*SimpleProject.myproj*，並尋找`Compile`項目。 每個`Compile`目標檔案，將檔案複製到新的專案資料夾。

  在衍生`SimpleProjectNode`類別會處理這些工作：

- 可讓專案和檔案中的節點的圖示**方案總管 中**来建立或選取。

- 可讓其他專案範本參數的替代項目來指定。

### <a name="to-extend-the-projectnode-class"></a>若要擴充 ProjectNode 類別

1. 新增類別，名為`SimpleProjectNode.cs`。

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

   這`SimpleProjectNode`類別實作有這些覆寫的方法：

- `ProjectGuid`它會傳回 project factory 的 GUID。

- `ProjectType`它會傳回此專案類型的當地語系化的名稱。

- `AddFileFromTemplate`其中將選取的檔案從 [範本] 資料夾複製到目的地專案。 在稍後的章節進一步實作這個方法。

  `SimpleProjectNode`建構函式，例如`SimpleProjectFactory`建構函式，會快取`SimpleProjectPackage`中供稍後使用的私用欄位的參考。

  連接`SimpleProjectFactory`類別，即可`SimpleProjectNode`類別，您必須具現化新`SimpleProjectNode`在`SimpleProjectFactory.CreateProject`方法並加以快取中供稍後使用的私用欄位。

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>若要連接的 project factory 類別與節點類別

1.  在  *SimpleProjectFactory.cs*檔案中，新增下列`using`陳述式：

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2.  取代`SimpleProjectFactory.CreateProject`方法藉由使用下列程式碼。

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3.  重建方案，並確認它建置無誤。

## <a name="test-the-projectnode-class"></a>測試 ProjectNode 類別
 測試您的專案處理站，以查看它是否會建立專案階層架構。

### <a name="to-test-the-projectnode-class"></a>若要測試 ProjectNode 類別

1.  按 **F5** 開始偵錯作業。 在實驗執行個體中，建立新的 SimpleProject。

2.  Visual Studio 應該呼叫您專案的處理站建立的專案。

3.  關閉 Visual Studio 的實驗執行個體。

## <a name="add-a-custom-project-node-icon"></a>加入自訂的專案節點圖示
 在前一節中的 [專案] 節點圖示是預設的圖示。 您可以將它變更自訂圖示。

### <a name="to-add-a-custom-project-node-icon"></a>若要加入自訂的專案節點圖示

1. 在 **資源**資料夾中，新增名為的點陣圖檔案*SimpleProjectNode.bmp*。

2. 在 **屬性**windows，減少為 16 x 16 像素的點陣圖。 請獨特的點陣圖。

    ![Simple Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. 在 **屬性**視窗中，變更**建置動作**點陣圖來**內嵌資源**。

4. 在  *SimpleProjectNode.cs*，新增下列`using`陳述式：

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. 將下列靜態欄位和建構函式來加入`SimpleProjectNode`類別。

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. 將下列屬性加入開頭`SimpleProjectNode`類別。

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. 取代為下列程式碼中的執行個體建構函式。

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

   在靜態的建構期間`SimpleProjectNode`擷取組件資訊清單資源的專案節點的點陣圖，並快取中供稍後使用的私用欄位。 請注意語法<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>映像路徑。 若要查看的資訊清單內嵌在組件中的資源名稱，請使用<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>方法。 當這個方法會套用至`SimpleProject`組件中，結果應該如下：

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  在執行個體建構期間`ProjectNode`基底類別載入*Resources.imagelis.bmp*中的內嵌常用於從 16 x 16 點陣圖*Resources\imagelis.bmp*。 此點陣圖清單會提供給`SimpleProjectNode`做為`ImageHandler.ImageList`。 `SimpleProjectNode` 將專案節點點陣圖附加至清單。 專案節點點陣圖影像清單中的位移會快取供稍後使用，做為公用值`ImageIndex`屬性。 Visual Studio 會使用這個屬性來判斷要顯示為 [專案] 節點圖示的點陣圖。

## <a name="test-the-custom-project-node-icon"></a>測試自訂專案節點圖示
 測試您的專案處理站，以查看它是否會建立專案階層中您自訂的專案節點的圖示。

### <a name="to-test-the-custom-project-node-icon"></a>若要測試自訂專案節點圖示

1.  開始偵錯，並在實驗執行個體中建立新的 SimpleProject。

2.  在新建的專案中，注意*SimpleProjectNode.bmp*做為專案節點圖示。

     ![簡單專案新增專案 節點](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3.  開啟*Program.cs*程式碼編輯器中。 您應該會看到類似下列的程式碼的原始程式碼。

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

     請注意，範本參數 $nameSpace$ 和 $ $className$ 不需要新的值。 您將學習如何實作在下一節中的範本參數替代。

## <a name="substitute-template-parameters"></a>取代範本參數
 在先前章節中，您的專案範本使用 Visual Studio 註冊使用`ProvideProjectFactory`屬性。 註冊範本資料夾的路徑，以這種方式可讓您覆寫，並展開，以啟用基本的範本參數替代`ProjectNode.AddFileFromTemplate`類別。 如需詳細資訊，請參閱[產生新專案：在幕後，第二部](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 現在將 取代程式碼加入`AddFileFromTemplate`類別。

### <a name="to-substitute-template-parameters"></a>若要取代範本參數

1. 在  *SimpleProjectNode.cs*檔案中，新增下列`using`陳述式。

   ```csharp
   using System.IO;
   ```

2. 取代`AddFileFromTemplate`方法藉由使用下列程式碼。

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

3. 設定在方法中，中斷點之後`className`指派陳述式。

   指派陳述式判斷命名空間和新的類別名稱的合理值。 這兩個`ProjectNode.FileTemplateProcessor.AddReplace`方法呼叫使用這些新值取代對應的範本參數值。

## <a name="test-the-template-parameter-substitution"></a>測試範本參數替代
 現在您可以測試範本參數替代。

### <a name="to-test-the-template-parameter-substitution"></a>若要測試的範本參數替代作業

1. 開始偵錯，並在實驗執行個體中建立新的 SimpleProject。

2. 中的中斷點處停止執行`AddFileFromTemplate`方法。

3. 檢查的值`nameSpace`和`className`參數。

   -   `nameSpace` 指定的值\<RootNamespace > 中的項目*\Templates\Projects\SimpleProject\SimpleProject.myproj*專案範本檔案。 此處的值為 `MyRootNamespace`。

   -   `className` 值會指定類別的來源檔案名稱，但不包括檔案名稱副檔名。 在此案例中，第一個檔案複製到目的資料夾是*AssemblyInfo.cs*; 因此，類別名稱的值是`AssemblyInfo`。

4. 移除中斷點，然後按**F5**繼續執行。

    Visual Studio 應該完成建立專案。

5. 開啟*Program.cs*程式碼編輯器中。 您應該會看到類似下列的程式碼的原始程式碼。

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

    請注意，命名空間現在`MyRootNamespace`和類別名稱現在是`Program`。

6. 開始偵錯專案。 新的專案應該編譯、 執行和顯示"Hello VSX!!!" 。

    ![簡單專案命令](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   恭喜您！ 您已實作的基本受管理的專案系統。