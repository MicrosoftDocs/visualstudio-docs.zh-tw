---
title: 建立基本的專案系統，第1部分 |Microsoft Docs
description: 瞭解如何建立名為 myproj.csproj 的專案類型。 在 Visual Studio 中，專案是用來組織原始程式碼檔和其他資產的容器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 15d28ff154629d07c643430b210d6106ac99978c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089429"
---
# <a name="create-a-basic-project-system-part-1"></a>建立基本的專案系統，第1部分
在 Visual Studio 中，專案是開發人員用來組織原始程式碼檔和其他資產的容器。 專案在 **方案總管** 中會顯示為解決方案的子系。 專案可讓您組織、建立、偵測和部署原始程式碼，以及建立 Web 服務、資料庫和其他資源的參考。

 專案是在專案檔中定義，例如 Visual c # 專案的 *.csproj* 檔。 您可以建立自己的專案類型，其擁有您自己的專案副檔名。 如需專案類型的詳細資訊，請參閱 [專案類型](../extensibility/internals/project-types.md)。

> [!NOTE]
> 如果您需要使用自訂的專案類型來擴充 Visual Studio，我們強烈建議您利用 [Visual Studio 專案系統](https://github.com/Microsoft/VSProjectSystem) (.vsps) ，它的優點比從頭建立專案系統有許多優點：
>
> - 更輕鬆上架。  即使是基本的專案系統，也需要數萬行程式碼。  利用 .VSPS 可在您準備好依據需求進行自訂之前，減少上線成本。
> - 維護更為容易。  利用 .VSPS，您只需要維護自己的案例。  我們會處理所有專案系統基礎結構的維護。
>
>   如果您需要將 Visual Studio 的版本設為高於 Visual Studio 2013 的版本，您將無法在 Visual Studio 擴充功能中利用 .VSPS。  如果是這種情況，這個逐步解說是開始使用的絕佳位置。

 本逐步解說將示範如何建立專案副檔名為 *myproj.csproj* 的專案類型。 本逐步解說會從現有的 Visual c # 專案系統中借用。

> [!NOTE]
> 如需擴充功能專案的範例，請參閱 [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

 本逐步解說會教您如何完成這些工作：

- 建立基本的專案類型。

- 建立基本專案範本。

- 向 Visual Studio 註冊專案範本。

- 開啟 [ **新增專案** ] 對話方塊，然後使用您的範本，以建立專案實例。

- 為您的專案系統建立專案 factory。

- 建立專案系統的專案節點。

- 新增專案系統的自訂圖示。

- 執行基本範本參數替代。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

 您也必須下載 [適用于專案的 Managed 封裝架構](https://github.com/tunnelvisionlabs/MPFProj10)原始程式碼。 將檔案解壓縮到您要建立的解決方案可存取的位置。

## <a name="create-a-basic-project-type"></a>建立基本的專案類型
 建立名為 **SimpleProject** 的 c # VSIX 專案。  (**檔案**  >  **新增**  >  **專案**，然後 **Visual c #** 擴充性  >    >  **VSIX 專案**) 。 在 **方案總管** 上新增 Visual Studio 套件專案專案範本 (，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]，然後移至 [擴充性]  >  **Visual Studio [封裝**]) 。 將檔案命名為 *SimpleProjectPackage*。

## <a name="creating-a-basic-project-template"></a>建立基本專案範本
 現在，您可以修改此基本 VSPackage 來執行 *myproj.csproj* 專案類型。 若要建立以 *myproj.csproj* 專案類型為基礎的專案，Visual Studio 必須知道要加入至新專案的檔案、資源和參考。 若要提供這項資訊，請將專案檔放在專案範本資料夾中。 當使用者使用 *myproj.csproj* 專案建立專案時，會將檔案複製到新專案。

### <a name="to-create-a-basic-project-template"></a>建立基本專案範本

1. 將三個資料夾新增到專案中，另一個是在另一個： *Templates\Projects\SimpleProject* 下。  (在 **方案總管** 中，以滑鼠右鍵按一下 [ **SimpleProject** ] 專案節點，指向 [新增 **]，然後** 按一下 [ **新增資料夾**]。 命名資料夾 *範本*。 在 [ *範本* ] 資料夾中，加入名為 [ *專案*] 的資料夾。 在 [ *專案* ] 資料夾中，加入名為 *SimpleProject* 的資料夾 ) 

2. 在 [ *Templates\Projects\SimpleProject* ] 資料夾中，加入點陣圖影像檔案，作為名為 *SimpleProject* 的圖示。 當您按一下 [ **新增**] 時，圖示編輯器隨即開啟。

3. 讓圖示成為特殊的。 此圖示將會在稍後的逐步解說中，出現在 [ **新增專案** ] 對話方塊中。

    ![簡單專案圖示](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. 儲存圖示並關閉圖示編輯器。

5. 在 [ *Templates\Projects\SimpleProject* ] 資料夾中，加入名為 *Program* 的 **類別** 專案。

6. 以下列程式程式碼取代現有的程式碼。

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
   > 這不是 *程式 .Cs 程式* 代碼的最終形式;取代參數將在稍後的步驟中處理。 您可能會看到編譯錯誤，但是只要檔案的 **BuildAction** 是 **內容**，您應該就可以像平常一樣地建立及執行專案。

7. 儲存檔案。

8. 從 *Properties* 資料夾將 *AssemblyInfo .cs* 檔案複製到 *Projects\SimpleProject* 資料夾。

9. 在 *Projects\SimpleProject* 資料夾中，加入名為 *SIMPLEPROJECT myproj.csproj* 的 XML 檔案。

   > [!NOTE]
   > 此類型之所有專案的副檔名為 *. myproj.csproj*。 如果您想要變更它，則必須在逐步解說中提及的所有位置進行變更。

10. 以下列程式程式碼取代現有的內容。

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

12. 在 [**屬性**] 視窗中，將 [ *AssemblyInfo*]、[ *SimpleProject*] 和 [ *SimpleProject* ] 的 [**組建] 動作** 設定為 [**內容** *]，並* 將其 [**包含于 VSIX** ] 屬性設定為 [ **True**]。

    此專案範本描述具有 Debug 設定和發行設定的基本 Visual c # 專案。 專案包含兩個原始程式檔： *AssemblyInfo .cs* 和 *Program .cs*，以及數個元件參考。 從範本建立專案時，會自動將 ProjectGuid 值取代為新的 GUID。

    在 **方案總管** 中，展開的 **範本** 資料夾應該會顯示如下：

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>建立基本的專案 factory
 您必須告訴 Visual Studio 專案範本資料夾的位置。 若要這樣做，請將屬性新增至 VSPackage 類別，以執行專案 factory，以便在建立 VSPackage 時，將範本位置寫入至系統登錄。 首先，建立由專案 factory GUID 所識別的基本專案 factory。 您 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 可以使用屬性將專案 factory 連接至 `SimpleProjectPackage` 類別。

### <a name="to-create-a-basic-project-factory"></a>建立基本的專案 factory

1. 為您的專案 factory 建立 Guid (在 [ **工具** ] 功能表上，按一下 [ **建立 GUID**) ]，或使用下列範例中的一個。 將 Guid 新增至 `SimpleProjectPackage` 已定義之區段附近的類別 `PackageGuidString` 。 Guid 必須同時為 GUID 格式和字串格式。 產生的程式碼應該類似于下列範例。

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. 將類別新增至名為 *SimpleProjectFactory* 的 top *SimpleProject* 資料夾。

3. 加入以下 using 指示詞：

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. 將 GUID 屬性加入至 `SimpleProjectFactory` 類別。 屬性的值是新的專案 factory GUID。

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   現在您可以註冊您的專案範本。

### <a name="to-register-the-project-template"></a>註冊專案範本

1. 在 *SimpleProjectPackage* 中，將屬性新增 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 至類別，如下所示 `SimpleProjectPackage` 。

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. 重建方案，並確認它是在沒有錯誤的情況下建立的。

    重建會註冊專案範本。

   參數 `defaultProjectExtension` 和 `possibleProjectExtensions` 會設定為專案檔名稱延伸 (*. myproj.csproj*) 。 `projectTemplatesDirectory`參數會設定為 [*範本*] 資料夾的相對路徑。 在組建期間，此路徑將會轉換成完整的組建，並新增至登錄以註冊專案系統。

## <a name="test-the-template-registration"></a>測試範本註冊
 範本註冊會告訴 Visual Studio 專案範本資料夾的位置，讓 Visual Studio 可以在 [ **新增專案** ] 對話方塊中顯示範本名稱和圖示。

### <a name="to-test-the-template-registration"></a>測試範本註冊

1. 按 **F5** 開始對 Visual Studio 的實驗性實例進行調試。

2. 在實驗實例中，建立新建立專案類型的新專案。 在 [**新增專案**] 對話方塊中，您應該會在 [**已安裝的範本**] 底下看到 **SimpleProject** 。

   現在您已有註冊的專案 factory。 不過，它還無法建立專案。 專案封裝和 project factory 會一起運作，以建立專案並加以初始化。

## <a name="add-the-managed-package-framework-code"></a>新增 Managed Package Framework 程式碼
 在專案封裝和專案處理站之間執行連接。

- 匯入 Managed Package Framework 的原始程式碼檔。

    1. 卸載 **方案總管** 中的 SimpleProject 專案 (，選取專案節點，然後在內容功能表上按一下 **[卸載專案**]，) 並在 XML 編輯器中開啟專案檔。

    2. 將下列區塊新增至專案檔 (在區塊) 的正上方 \<Import> 。 設定 `ProjectBasePath` 為您剛剛下載的 Managed Package Framework 程式碼中 *ProjectBase* 檔案的位置。 您可能必須在路徑名稱加上反斜線。 如果沒有，專案可能會找不到 Managed Package Framework 原始程式碼。

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > 請不要忘記路徑結尾的反斜線。

    3. 重載專案。

    4. 加入下列組件的參考：

        - `Microsoft.VisualStudio.Designer.Interfaces`*\<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*) 中的 (

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>若要初始化專案 factory

1. 在 *SimpleProjectPackage .cs* 檔案中，加入下列指示詞 `using` 。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. 從衍生 `SimpleProjectPackage` 類別 `Microsoft.VisualStudio.Package.ProjectPackage` 。

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. 註冊 project factory。 將下列程式程式碼新增至 `SimpleProjectPackage.Initialize` 方法（緊接在之後） `base.Initialize` 。

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. 執行抽象屬性 `ProductUserContext` ：

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. 在 *SimpleProjectFactory* 中，將下列指示詞新增至現有指示詞 `using` 之後 `using` 。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. 從衍生 `SimpleProjectFactory` 類別 `ProjectFactory` 。

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. 將下列虛擬方法新增至 `SimpleProjectFactory` 類別。 您將在稍後的章節中執行此方法。

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. 將下欄欄位和函式加入至 `SimpleProjectFactory` 類別。 此 `SimpleProjectPackage` 參考會快取在私用欄位中，以供用來設定服務提供者網站。

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. 重建方案，並確認它是在沒有錯誤的情況下建立的。

## <a name="test-the-project-factory-implementation"></a>測試 project factory 的執行
 測試是否呼叫您的專案 factory 執行的函式。

### <a name="to-test-the-project-factory-implementation"></a>測試 project factory 的執行

1. 在 *SimpleProjectFactory .cs* 檔案的函式中，于下一行設定中斷點 `SimpleProjectFactory` 。

    ```csharp
    this.package = package;
    ```

2. 按 **F5** 以啟動 Visual Studio 的實驗實例。

3. 在實驗實例中，開始建立新專案。 在 [ **新增專案** ] 對話方塊中，選取 [ **SimpleProject** ] 專案類型，然後按一下 **[確定]**。 執行會在中斷點停止。

4. 清除中斷點，然後停止調試。 由於我們尚未建立專案節點，因此專案建立程式碼仍會擲回例外狀況。

## <a name="extend-the-projectnode-class"></a>擴充 ProjectNode 類別
 現在您可以執行 `SimpleProjectNode` 衍生自類別的類別 `ProjectNode` 。 `ProjectNode`基底類別會處理專案建立的下列工作：

- 將專案範本檔 SimpleProject （ *myproj.csproj*）複製到新的專案資料夾。 複本會根據在 [ **新增專案** ] 對話方塊中輸入的名稱重新命名。 `ProjectGuid`屬性值會取代為新的 GUID。

- 遍歷專案範本檔案的 MSBuild 專案（ *SimpleProject. myproj.csproj*），並尋找 `Compile` 元素。 針對每個 `Compile` 目標檔案，將檔案複製到新的專案資料夾。

  衍生的 `SimpleProjectNode` 類別會處理下列工作：

- 針對要建立或選取 **方案總管** 中的專案和檔案節點啟用圖示。

- 啟用要指定的其他專案範本參數替代專案。

### <a name="to-extend-the-projectnode-class"></a>擴充 ProjectNode 類別

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

   這個 `SimpleProjectNode` 類別的實有下列覆寫的方法：

- `ProjectGuid`，會傳回專案 factory GUID。

- `ProjectType`，傳回專案類型的當地語系化名稱。

- `AddFileFromTemplate`，這會將選取的檔案從範本資料夾複製到目的地專案。 這個方法會在稍後的章節中進一步執行。

  如同函式一樣，此函式會 `SimpleProjectNode` `SimpleProjectFactory` `SimpleProjectPackage` 在私用欄位中快取參考，以供稍後使用。

  若要將 `SimpleProjectFactory` 類別連接至 `SimpleProjectNode` 類別，您必須在方法中具現化新的，並將它快取 `SimpleProjectNode` `SimpleProjectFactory.CreateProject` 在私用欄位中，以供稍後使用。

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>連接專案 factory 類別和 node 類別

1. 在 *SimpleProjectFactory .cs* 檔案中，加入下列指示詞 `using` ：

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. `SimpleProjectFactory.CreateProject`使用下列程式碼取代方法。

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. 重建方案，並確認它是在沒有錯誤的情況下建立的。

## <a name="test-the-projectnode-class"></a>測試 ProjectNode 類別
 測試您的 project factory，以查看它是否會建立專案階層。

### <a name="to-test-the-projectnode-class"></a>測試 ProjectNode 類別

1. 按 **F5** 開始偵錯。 在實驗實例中，建立新的 SimpleProject。

2. Visual Studio 應呼叫您的 project factory 以建立專案。

3. 關閉 Visual Studio 的實驗執行個體。

## <a name="add-a-custom-project-node-icon"></a>新增自訂專案節點圖示
 先前章節中的專案節點圖示為預設圖示。 您可以將它變更為自訂圖示。

### <a name="to-add-a-custom-project-node-icon"></a>新增自訂專案節點圖示

1. 在 [ **資源** ] 資料夾中，加入名為 *SimpleProjectNode.bmp* 的點陣圖檔案。

2. 在 [ **屬性** ] 視窗中，將點陣圖減少為 16 x 16 圖元。 讓點陣圖具有特色。

    ![簡單專案 Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. 在 [ **屬性** ] 視窗中，將點陣圖的 [ **建立] 動作** 變更為 [ **內嵌資源**]。

4. 在 *SimpleProjectNode* 中，新增下列指示詞 `using` ：

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. 將下列靜態欄位和函式加入至 `SimpleProjectNode` 類別。

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. 將下列屬性加入至類別的開頭 `SimpleProjectNode` 。

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. 以下列程式碼取代實例的函式。

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

   在靜態結構期間， `SimpleProjectNode` 會從組件資訊清單資源抓取專案節點點陣圖，並將其快取在私用欄位中，以供稍後使用。 請注意 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 影像路徑的語法。 若要查看內嵌在元件中的資訊清單資源名稱，請使用 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 方法。 當此方法套用至元件時 `SimpleProject` ，結果應該如下所示：

- *SimpleProject 資源*

- *VisualStudio*

- *SimpleProject. VSPackage 資源*

- *Resources.imagelis.bmp*

- *VisualStudio. DontShowAgainDialog. 資源*

- *VisualStudio. SecurityWarningDialog. 資源*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  在實例結構期間， `ProjectNode` 基類會載入 *Resources.imagelis.bmp*，其中內嵌常用於 *Resources\imagelis.bmp* 的 16 x 16 點陣圖。 此點陣圖清單可供使用， `SimpleProjectNode` 如下所示 `ImageHandler.ImageList` 。 `SimpleProjectNode` 將專案節點點陣圖附加至清單。 會快取影像清單中專案節點點陣圖的位移，以供稍後用作公用屬性的值 `ImageIndex` 。 Visual Studio 使用這個屬性來決定要顯示為專案節點圖示的點陣圖。

## <a name="test-the-custom-project-node-icon"></a>測試自訂專案節點圖示
 測試您的 project factory，看看它是否建立了具有您自訂專案節點圖示的專案階層。

### <a name="to-test-the-custom-project-node-icon"></a>測試自訂專案節點圖示

1. 開始調試，並在實驗實例中建立新的 SimpleProject。

2. 在新建立的專案中，請注意， *SimpleProjectNode.bmp* 會當做專案節點圖示使用。

     ![簡單專案新增專案節點](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. 在程式碼編輯器中開啟 *Program.cs*。 您應該會看到類似下列程式碼的原始程式碼。

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

     請注意，$nameSpace $ 和 $className $ 的範本參數沒有新的值。 您將在下一節中瞭解如何執行範本參數替代。

## <a name="substitute-template-parameters"></a>替代範本參數
 在先前的章節中，您已使用屬性向 Visual Studio 註冊專案範本 `ProvideProjectFactory` 。 以這種方式註冊範本資料夾的路徑，可讓您藉由覆寫和展開類別來啟用基本範本參數替代 `ProjectNode.AddFileFromTemplate` 。 如需詳細資訊，請參閱 [新專案產生：幕後的第二部分](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 現在將取代程式碼新增至 `AddFileFromTemplate` 類別。

### <a name="to-substitute-template-parameters"></a>替代範本參數

1. 在 *SimpleProjectNode .cs* 檔案中，加入下列指示詞 `using` 。

   ```csharp
   using System.IO;
   ```

2. `AddFileFromTemplate`使用下列程式碼取代方法。

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

3. 在方法中設定中斷點，緊接在 `className` 指派語句之後。

   指派語句會判斷命名空間的合理值和新的類別名稱。 這兩個 `ProjectNode.FileTemplateProcessor.AddReplace` 方法呼叫會使用這些新值來取代對應的範本參數值。

## <a name="test-the-template-parameter-substitution"></a>測試範本參數替代
 現在您可以測試範本參數替代。

### <a name="to-test-the-template-parameter-substitution"></a>測試範本參數替代

1. 開始調試，並在實驗實例中建立新的 SimpleProject。

2. 執行會在方法的中斷點停止執行 `AddFileFromTemplate` 。

3. 檢查和參數的值 `nameSpace` `className` 。

   - `nameSpace` 會提供 \<RootNamespace> *\Templates\Projects\SimpleProject\SimpleProject.myproj* 專案範本檔中的元素值。 此處的值為 `MyRootNamespace`。

   - `className` 提供類別原始程式檔名稱的值，但不含副檔名。 在此情況下，要複製到目的資料夾的第一個檔案是 *AssemblyInfo .cs*;因此，className 的值為 `AssemblyInfo` 。

4. 移除中斷點，然後按 **F5** 繼續執行。

    Visual Studio 應完成專案的建立。

5. 在程式碼編輯器中開啟 *Program.cs*。 您應該會看到類似下列程式碼的原始程式碼。

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

    請注意，命名空間現在是 `MyRootNamespace` ，類別名稱現在是 `Program` 。

6. 開始進行專案偵錯。 新的專案應該編譯、執行，並顯示 "Hello VSX!!!" 。

    ![簡單專案命令](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   恭喜！ 您已執行基本的 managed 專案系統。
