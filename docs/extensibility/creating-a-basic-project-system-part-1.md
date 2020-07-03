---
title: 建立基本的專案系統，第1部分 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: e95f760712f46632120540091b9f8f408aad9da4
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903427"
---
# <a name="create-a-basic-project-system-part-1"></a>建立基本的專案系統，第1部分
在 Visual Studio 中，專案是開發人員用來組織原始程式碼檔案和其他資產的容器。 專案會在**方案總管**中顯示為解決方案的子系。 專案可讓您組織、建立、偵測和部署原始程式碼，並建立 Web 服務、資料庫和其他資源的參考。

 專案是在專案檔中定義，例如 Visual c # 專案的 *.csproj*檔案。 您可以建立自己的專案類型，其具有您自己的專案副檔名。 如需專案類型的詳細資訊，請參閱[專案類型](../extensibility/internals/project-types.md)。

> [!NOTE]
> 如果您需要使用自訂的專案類型來擴充 Visual Studio，強烈建議您使用[Visual Studio 專案系統](https://github.com/Microsoft/VSProjectSystem)（.vsps），其具有比從頭建立專案系統更多的優點：
>
> - 更輕鬆的上架。  即使是基本的專案系統，還是需要數十行程式碼。  利用 .VSPS 可在您準備好自訂您的需求之前，先按幾下就能減少上架成本。
> - 維護更容易。  藉由利用 .VSPS，您只需要維護自己的案例。  我們會處理所有專案系統基礎結構的維護。
>
>   如果您需要以早于 Visual Studio 2013 的 Visual Studio 版本為目標，您將無法利用 Visual Studio 擴充功能中的 .VSPS。  如果是這種情況，則此逐步解說是開始使用的絕佳位置。

 本逐步解說將示範如何建立具有專案檔副檔名*myproj.csproj*的專案類型。 此逐步解說會從現有的 Visual c # 專案系統中借用。

> [!NOTE]
> 如需擴充功能專案的更多範例，請參閱[VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

 本逐步解說將教您如何完成這些工作：

- 建立基本的專案類型。

- 建立基本的專案範本。

- 向 Visual Studio 註冊專案範本。

- 開啟 [**新增專案**] 對話方塊，然後使用您的範本，以建立專案實例。

- 為您的專案系統建立專案 factory。

- 建立專案系統的專案節點。

- 加入專案系統的自訂圖示。

- 執行基本範本參數替代。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

 您也必須下載[適用于專案的 Managed 封裝架構](https://github.com/tunnelvisionlabs/MPFProj10)原始程式碼。 將檔案解壓縮到您即將建立之解決方案可存取的位置。

## <a name="create-a-basic-project-type"></a>建立基本專案類型
 建立名為**SimpleProject**的 c # VSIX 專案。 （**File**  > **新增**  > **專案**，然後是**Visual c #** 擴充性  >  **Extensibility**  >  **VSIX 專案**）。 加入 Visual Studio 封裝專案專案範本（在**方案總管**上，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]，然後**Extensibility**移至 [擴充性] [  >  **Visual Studio 封裝**]）。 將檔案命名為*SimpleProjectPackage*。

## <a name="creating-a-basic-project-template"></a>建立基本專案範本
 現在，您可以修改此基本 VSPackage，以執行*myproj.csproj*專案類型。 若要建立以*myproj.csproj*專案類型為基礎的專案，Visual Studio 必須知道要將哪些檔案、資源和參考加入至新專案。 若要提供這項資訊，請將專案檔案放在專案範本資料夾中。 當使用者使用*myproj.csproj*專案來建立專案時，檔案會複製到新的專案。

### <a name="to-create-a-basic-project-template"></a>建立基本專案範本

1. 在專案中新增三個資料夾，其中一個位於 [另一個： *Templates\Projects\SimpleProject*] 底下。 （在**方案總管**中，以滑鼠右鍵按一下**SimpleProject**專案節點，指向 [**加入**]，然後按一下 [**新增資料夾**]。 將資料夾命名為*範本*。 在 [*範本*] 資料夾中，新增名為 [*專案*] 的資料夾。 在 [*專案*] 資料夾中，新增名為*SimpleProject*的資料夾。）

2. 在*Templates\Projects\SimpleProject*資料夾中，新增點陣圖影像檔案，以作為名為*SimpleProject*的圖示。 當您按一下 [**新增**] 時，圖示編輯器隨即開啟。

3. 讓圖示與眾不同。 這個圖示稍後會出現在逐步解說的 [**新增專案**] 對話方塊中。

    ![簡單專案圖示](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. 儲存圖示並關閉圖示編輯器。

5. 在*Templates\Projects\SimpleProject*資料夾中，新增名為*Program.cs*的**類別**專案。

6. 將現有的程式碼取代為下列幾行。

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
   > 這不是*Program.cs*程式碼的最終形式;取代參數將會在稍後的步驟中處理。 您可能會看到編譯錯誤，但是只要檔案的**BuildAction**是**內容**，您就應該能夠照常建立並執行專案。

7. 儲存檔案。

8. 將*AssemblyInfo.cs*檔案從*Properties*資料夾複製到*Projects\SimpleProject*資料夾。

9. 在*Projects\SimpleProject*資料夾中，新增名為*SimpleProject. myproj.csproj*的 XML 檔案。

   > [!NOTE]
   > 此類型之所有專案的副檔名為 *. myproj.csproj*。 如果您想要變更它，您必須在逐步解說中提到的任何地方變更它。

10. 以下列幾行取代現有的內容。

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

12. 在 [**屬性**] 視窗中，將 [ *AssemblyInfo.cs*]、[ *Program.cs*]、[ *SimpleProject*] 和 [ *SimpleProject* ] 的**組建動作**設定為 [**內容**]，並將其 [**在 VSIX 屬性中包含**] 設定為 [ **True**]。

    此專案範本說明基本的 Visual c # 專案，其中同時具有「偵錯工具」設定和「發行」設定。 此專案包含兩個原始程式檔： *AssemblyInfo.cs*和*Program.cs*，以及數個元件參考。 從範本建立專案時，ProjectGuid 值會自動取代為新的 GUID。

    在**方案總管**中，展開的 [**範本**] 資料夾應該會如下所示：

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
 您必須告訴 Visual Studio 專案範本資料夾的位置。 若要這樣做，請將屬性新增至 VSPackage 類別，以執行專案 factory，讓範本位置在建立 VSPackage 時寫入至系統登錄。 首先，建立由專案 factory GUID 所識別的基本專案 factory。 使用 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 屬性將專案 factory 連接至 `SimpleProjectPackage` 類別。

### <a name="to-create-a-basic-project-factory"></a>建立基本的專案 factory

1. 建立專案處理站的 Guid （在 [**工具**] 功能表上，按一下 [**建立 GUID**]），或使用下列範例中的一個。 將 Guid 加入至 `SimpleProjectPackage` 已定義之區段附近的類別 `PackageGuidString` 。 Guid 必須同時為 GUID 格式和字串形式。 產生的程式碼應該類似下列範例。

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. 將類別新增至名為*SimpleProjectFactory.cs*的頂端*SimpleProject*資料夾。

3. 加入以下 using 指示詞：

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. 將 GUID 屬性新增至 `SimpleProjectFactory` 類別。 屬性的值是新的專案 factory GUID。

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   您現在可以註冊您的專案範本。

### <a name="to-register-the-project-template"></a>若要註冊專案範本

1. 在*SimpleProjectPackage.cs*中，將 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 屬性新增至 `SimpleProjectPackage` 類別，如下所示。

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. 重建方案，並確認它的組建不會發生錯誤。

    重建會註冊專案範本。

   參數 `defaultProjectExtension` 和 `possibleProjectExtensions` 會設定為專案檔的副檔名（*. myproj.csproj*）。 `projectTemplatesDirectory`參數會設定為 [*範本*] 資料夾的相對路徑。 在組建期間，此路徑將會轉換成完整組建並新增到登錄中，以註冊專案系統。

## <a name="test-the-template-registration"></a>測試範本註冊
 範本註冊會告訴 Visual Studio 專案範本資料夾的位置，讓 Visual Studio 可以在 [**新增專案**] 對話方塊中顯示範本名稱和圖示。

### <a name="to-test-the-template-registration"></a>測試範本註冊

1. 按**F5**開始對 Visual Studio 的實驗實例進行偵錯工具。

2. 在實驗實例中，為新建立的專案類型建立新的專案。 在 [**新增專案**] 對話方塊中，您應該會在 [**已安裝的範本**] 底下看到**SimpleProject** 。

   現在您已有註冊的專案 factory。 不過，它還無法建立專案。 專案封裝和專案 factory 會一起工作，以建立和初始化專案。

## <a name="add-the-managed-package-framework-code"></a>新增 Managed Package Framework 程式碼
 執行專案封裝與專案 factory 之間的連接。

- 匯入 Managed 封裝架構的原始程式碼檔案。

    1. 卸載 SimpleProject 專案（在**方案總管**中，選取專案節點，然後在內容功能表上按一下 **[卸載專案**]），然後在 XML 編輯器中開啟專案檔。

    2. 將下列區塊新增至專案檔（在區塊的正上方 \<Import> ）。 將設定 `ProjectBasePath` 為您剛才下載之 Managed Package Framework 程式碼中的*ProjectBase*檔案位置。 您可能必須在路徑名稱中加上反斜線。 如果不這麼做，專案可能會找不到 Managed Package Framework 原始程式碼。

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

        - `Microsoft.VisualStudio.Designer.Interfaces`（在* \<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*中）

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>若要初始化專案 factory

1. 在*SimpleProjectPackage.cs*檔案中，新增下列指示詞 `using` 。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. 從衍生 `SimpleProjectPackage` 類別 `Microsoft.VisualStudio.Package.ProjectPackage` 。

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. 註冊專案 factory。 將下列程式程式碼新增至 `SimpleProjectPackage.Initialize` 方法，緊接在之後 `base.Initialize` 。

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

5. 在*SimpleProjectFactory.cs*中，將下列指示詞新增至現有指示詞 `using` 之後 `using` 。

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. 從衍生 `SimpleProjectFactory` 類別 `ProjectFactory` 。

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. 將下列虛擬方法新增至 `SimpleProjectFactory` 類別。 您將在稍後的區段中執行此方法。

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. 將下欄欄位和構造函式新增至 `SimpleProjectFactory` 類別。 此 `SimpleProjectPackage` 參考會在私用欄位中快取，以便用來設定服務提供者網站。

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. 重建方案，並確認它的組建不會發生錯誤。

## <a name="test-the-project-factory-implementation"></a>測試專案 factory 的執行
 測試是否呼叫您的專案 factory 實作為函式。

### <a name="to-test-the-project-factory-implementation"></a>測試專案 factory 的執行

1. 在*SimpleProjectFactory.cs*檔案中，于函式的下列程式程式碼上設定中斷點 `SimpleProjectFactory` 。

    ```csharp
    this.package = package;
    ```

2. 按**F5**啟動 Visual Studio 的實驗實例。

3. 在實驗實例中，開始建立新的專案。 在 [**新增專案**] 對話方塊中，選取 [ **SimpleProject** ] 專案類型，然後按一下 **[確定]**。 執行會在中斷點停止。

4. 清除中斷點並停止調試。 由於我們尚未建立專案節點，因此專案建立程式碼仍然會擲回例外狀況。

## <a name="extend-the-projectnode-class"></a>擴充 ProjectNode 類別
 現在您可以執行 `SimpleProjectNode` 衍生自類別的類別 `ProjectNode` 。 `ProjectNode`基類會處理專案建立作業的下列工作：

- 將專案範本檔案（ *SimpleProject. myproj.csproj*）複製到新的專案資料夾。 該複本會根據 [**新增專案**] 對話方塊中所輸入的名稱重新命名。 `ProjectGuid`屬性值會由新的 GUID 取代。

- 會遍歷專案範本檔案的 MSBuild 元素*SimpleProject. myproj.csproj*，並尋找 `Compile` 元素。 針對每個 `Compile` 目標檔案，將檔案複製到新的專案資料夾。

  衍生的 `SimpleProjectNode` 類別會處理下列工作：

- 啟用**方案總管**中要建立或選取之專案和檔案節點的圖示。

- 啟用要指定的其他專案範本參數替代。

### <a name="to-extend-the-projectnode-class"></a>若要擴充 ProjectNode 類別

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

   這個 `SimpleProjectNode` 類別的實作為這些覆寫的方法：

- `ProjectGuid`，它會傳回專案 factory GUID。

- `ProjectType`，它會傳回專案類型的當地語系化名稱。

- `AddFileFromTemplate`，這會將選取的檔案從範本資料夾複製到目的地專案。 這個方法會在稍後的章節中進一步執行。

  如同函式，此函式會快取 `SimpleProjectNode` `SimpleProjectFactory` 私用 `SimpleProjectPackage` 欄位中的參考以供稍後使用。

  若要將 `SimpleProjectFactory` 類別連接至 `SimpleProjectNode` 類別，您必須在方法中具現化新的，並將它快取 `SimpleProjectNode` `SimpleProjectFactory.CreateProject` 在私用欄位中，以供稍後使用。

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>若要連接 project factory 類別和 node 類別

1. 在*SimpleProjectFactory.cs*檔案中，新增下列指示詞 `using` ：

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

3. 重建方案，並確認它的組建不會發生錯誤。

## <a name="test-the-projectnode-class"></a>測試 ProjectNode 類別
 測試您的專案 factory，以查看它是否建立專案階層。

### <a name="to-test-the-projectnode-class"></a>測試 ProjectNode 類別

1. 按 **F5** 開始偵錯。 在實驗實例中，建立新的 SimpleProject。

2. Visual Studio 應該呼叫您的專案 factory 來建立專案。

3. 關閉 Visual Studio 的實驗執行個體。

## <a name="add-a-custom-project-node-icon"></a>新增自訂專案節點圖示
 先前區段中的專案節點圖示是預設圖示。 您可以將它變更為自訂圖示。

### <a name="to-add-a-custom-project-node-icon"></a>若要加入自訂專案節點圖示

1. 在 [**資源**] 資料夾中，新增名為*SimpleProjectNode.bmp*的點陣圖檔案。

2. 在 [**屬性**] 視窗中，將點陣圖減少為 16 x 16 圖元。 讓點陣圖與眾不同。

    ![簡單專案 Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. 在 [**屬性**] 視窗中，將點陣圖的 [**組建] 動作**變更為 [**內嵌資源**]。

4. 在*SimpleProjectNode.cs*中，新增下列指示詞 `using` ：

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. 將下列靜態欄位和構造函式新增至 `SimpleProjectNode` 類別。

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. 將下列屬性新增至類別的開頭 `SimpleProjectNode` 。

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. 將實例的函式取代為下列程式碼。

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

   在靜態結構中， `SimpleProjectNode` 會從組件資訊清單資源抓取專案節點點陣圖，並將其快取到私用欄位以供稍後使用。 請注意 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 影像路徑的語法。 若要查看內嵌在元件中的資訊清單資源名稱，請使用 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 方法。 當此方法套用至元件時 `SimpleProject` ，其結果應如下所示：

- *SimpleProject .resources*

- *VisualStudio 資源*

- *SimpleProject. VSPackage. resources*

- *Resources.imagelis.bmp*

- *VisualStudio. DontShowAgainDialog .resources*

- *VisualStudio. SecurityWarningDialog .resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  在實例結構中， `ProjectNode` 基底類別會載入*Resources.imagelis.bmp*，其中內嵌常用於*Resources\imagelis.bmp*的 16 x 16 個位圖。 這個點陣圖清單可供做 `SimpleProjectNode` 為 `ImageHandler.ImageList` 。 `SimpleProjectNode`將專案節點點陣圖附加至清單。 影像清單中的專案節點點陣圖位移會被快取，以供稍後用來做為公用屬性的值 `ImageIndex` 。 Visual Studio 使用這個屬性來決定要顯示哪一個點陣圖做為專案節點圖示。

## <a name="test-the-custom-project-node-icon"></a>測試自訂專案節點圖示
 測試您的專案 factory，以查看它是否會建立具有您自訂專案節點圖示的專案階層。

### <a name="to-test-the-custom-project-node-icon"></a>測試自訂專案節點圖示

1. 開始進行調試，並在實驗實例中建立新的 SimpleProject。

2. 請注意，在新建立的專案中，會使用*SimpleProjectNode.bmp*做為專案節點圖示。

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

     請注意，範本參數 $nameSpace $ 和 $className $ 沒有新的值。 在下一節中，您將瞭解如何執行範本參數替代。

## <a name="substitute-template-parameters"></a>替代範本參數
 在先前的章節中，您已使用屬性，向 Visual Studio 註冊專案範本 `ProvideProjectFactory` 。 以這種方式註冊範本資料夾的路徑，可讓您覆寫並展開類別，以啟用基本範本參數替代 `ProjectNode.AddFileFromTemplate` 。 如需詳細資訊，請參閱[新的專案產生：在幕後，第二部分](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 現在，將取代程式碼加入至 `AddFileFromTemplate` 類別。

### <a name="to-substitute-template-parameters"></a>替代範本參數

1. 在*SimpleProjectNode.cs*檔案中，新增下列指示詞 `using` 。

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

   指派語句會決定命名空間的合理值和新的類別名稱。 這兩個 `ProjectNode.FileTemplateProcessor.AddReplace` 方法呼叫會使用這些新的值來取代對應的範本參數值。

## <a name="test-the-template-parameter-substitution"></a>測試範本參數替代
 現在您可以測試範本參數替代。

### <a name="to-test-the-template-parameter-substitution"></a>測試範本參數替代

1. 開始進行調試，並在實驗實例中建立新的 SimpleProject。

2. 執行會在方法中的中斷點停止 `AddFileFromTemplate` 。

3. 檢查和參數的值 `nameSpace` `className` 。

   - `nameSpace`會提供 \<RootNamespace> *\Templates\Projects\SimpleProject\SimpleProject.myproj*專案範本檔案中元素的值。 此處的值為 `MyRootNamespace`。

   - `className`會提供類別來原始檔案名的值，但不含副檔名。 在此情況下，要複製到目的資料夾的第一個檔案是*AssemblyInfo.cs*;因此，className 的值是 `AssemblyInfo` 。

4. 請移除中斷點，然後按**F5**繼續執行。

    Visual Studio 應該會完成專案的建立。

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

    請注意，命名空間現在是 `MyRootNamespace` ，而類別名稱現在是 `Program` 。

6. 開始進行專案偵錯。 新的專案應該會編譯、執行和顯示 "Hello VSX!!!" 。

    ![簡單專案命令](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   恭喜！ 您已實作為基本的受控專案系統。
