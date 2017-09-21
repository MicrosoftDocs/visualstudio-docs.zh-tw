---
title: "建立基本專案系統，第 1 部分 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "撰寫專案系統"
  - "專案系統"
  - "教學課程"
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 47
---
# 建立基本專案系統，第 1 部分
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中，專案會是開發人員用來組織原始程式碼檔和其他資產的容器。 專案會顯示為子系中的解決方案 **方案總管\] 中**。 專案可讓您組織、 建置、 偵錯和部署原始程式碼和建立 Web 服務、 資料庫和其他資源的參考。  
  
 專案被定義在專案檔，例如 Visual C\# 專案的.csproj 檔案。 您可以建立您自己副檔名自己專案的專案類型。 如需專案類型的詳細資訊，請參閱 [專案類型](../extensibility/internals/project-types.md)。  
  
> [!NOTE]
>  如果您需要擴充 Visual Studio 的自訂專案類型，我們強烈建議運用 [Visual Studio 專案系統](https://github.com/Microsoft/VSProjectSystem) 有許多地建立全新的專案系統的優勢︰  
>   
>  -   簡單的上架。  即使基本專案系統會要求數萬個幾行程式碼。  運用 CPS 降低上架幾個按鍵動作之後，您可以自訂自己的需求。  
> -   更容易維護。  利用 CPS，您只需要維護您自己的案例。  我們會處理所有的專案系統基礎結構的保養。  
>   
>  如果您需要版本早於 Visual Studio 2013 的 Visual Studio 為目標，您無法將 CPS 運用在 Visual Studio 擴充功能。  如果是這樣，本逐步解說是不錯的起點開始。  
  
 本逐步解說會示範如何建立具有專案檔案名稱副檔名.myproj 的專案類型。 本逐步解說借用現有的 Visual C\# 專案系統。  
  
> [!NOTE]
>  如需完整的語言專案系統的端對端範例，請參閱 IronPython 範例深入了解在 [VSSDK 範例](../misc/vssdk-samples.md)。  
  
 這個逐步解說示範如何完成這些工作︰  
  
-   建立基本專案類型。  
  
-   建立基本專案範本。  
  
-   註冊 Visual Studio 專案範本。  
  
-   建立專案的執行個體開啟 **新的專案** \] 對話方塊中，然後使用您的範本。  
  
-   建立您的專案系統的專案處理站。  
  
-   建立您的專案系統的專案節點。  
  
-   新增自訂圖示的專案系統。  
  
-   實作基本的範本參數替代。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 您還必須下載的程式碼 [Managed 專案的封裝 Framework](http://mpfproj12.codeplex.com/)。 將檔案解壓縮至您要建立的方案存取的位置。  
  
## 建立基本專案類型  
 建立 C\# VSIX 專案，名為 **SimpleProject**。 \(**檔案\]、 \[新增\]、 \[專案** 然後 **C\# 中，擴充性，Visual Studio 套件**\)。 加入 Visual Studio Package 專案項目範本 \(在 \[方案總管\] 中，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**, ，然後移至 **擴充性 \/ Visual Studio 套件**\)。 將檔案命名 **SimpleProjectPackage**。  
  
## 建立基本專案範本  
 現在，您可以修改此基本 VSPackage 來實作新的.myproj 專案類型。 若要建立.myproj 專案類型為基礎的專案，Visual Studio 必須知道哪些檔案、 資源及加入新的專案參考。 若要提供這項資訊，請將專案檔案專案範本資料夾中。 當使用者使用.myproj 專案建立專案時，檔案會複製到新的專案。  
  
#### 若要建立基本專案範本  
  
1.  加入至專案，其中一個之下的三個資料夾︰ **Templates\\Projects\\SimpleProject**。 \(在 **方案總管\] 中**, ，以滑鼠右鍵按一下 **SimpleProject** 專案節點，指向 **新增**, ，然後按一下 \[ **新資料夾**。 將資料夾命名為 `Templates`。 在 **範本** 資料夾中，新增名為 `Projects`。 在 **專案** 資料夾中，新增名為 `SimpleProject`。\)  
  
2.  在 **Projects\\SimpleProject** 資料夾加入圖示檔名為 `SimpleProject.ico`。 當您按一下 **新增**, ，圖示編輯器隨即開啟。  
  
3.  請特殊圖示。 這個圖示會出現在 **新的專案** 逐步解說稍後的對話方塊。  
  
     ![簡單專案圖示](~/extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  儲存圖示，並關閉編輯器\] 圖示。  
  
5.  在 **Projects\\SimpleProject** 資料夾中，加入 **類別** 項目，稱為 `Program.cs`。  
  
6.  使用下列程式碼行取代現有的程式碼。  
  
    ```c#  
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
    >  這不是最終形式 Program.cs 程式碼;取代參數會處理在稍後的步驟。 您可能會看到編譯錯誤，但只要檔案 **BuildAction** 是 **內容**, ，您應該能夠建置並執行專案，如往常般。  
  
1.  儲存檔案。  
  
2.  AssemblyInfo.cs 檔案複製 **屬性** 資料夾 **Projects\\SimpleProject** 資料夾。  
  
3.  在 **Projects\\SimpleProject** 資料夾加入 XML 檔，名為 `SimpleProject.myproj`。  
  
    > [!NOTE]
    >  此類型的所有專案的副檔名是.myproj。 如果您想要變更它，您必須變更它被提及的逐步解說中的每個地方。  
  
4.  將現有的內容取代下列程式碼行。  
  
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
  
5.  儲存檔案。  
  
6.  在 **屬性** 視窗中，設定 **建置動作** AssemblyInfo.cs、 Program.cs、 SimpleProject.ico，和以 SimpleProject.myproj **內容**, ，並設定其 **Include in VSIX** 屬性，以 **True**。  
  
 這個專案範本描述基本 Visual C\# 專案的偵錯組態和發行組態。 專案包含兩個原始程式檔、 AssemblyInfo.cs 和 Program.cs 和數個組件的參考。 從範本建立專案時，ProjectGuid 值都會自動取代新的 GUID。  
  
 在 **方案總管\] 中**, ，展開 **範本** 資料夾應該會出現，如下所示︰  
  
 範本  
  
 專案  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## 建立基本專案 Factory  
 您必須告訴 Visual Studio 專案範本資料夾的位置。 若要這樣做，請新增實作專案 factory，因此範本位置時，寫入系統登錄建立 VSPackage 的 VSPackage 類別的屬性。 開始建立基本專案處理站所識別的專案的處理站的 GUID。 使用 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 專案 factory 連 SimpleProjectPackage 類別的屬性。  
  
#### 若要建立基本專案 factory  
  
1.  程式碼編輯器中開啟 SimpleProjectPackageGuids.cs。  
  
2.  為您專案的 factory 建立 Guid \(上 **工具** \] 功能表上，按一下 \[ **建立 GUID**\)，或使用下列範例中的一個。 將 Guid 加入至 SimpleProjectPackageGuids 類別。 GUID 格式和字串格式必須是 Guid。 產生的程式碼應該類似下列的範例。  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  將類別加入至頂端 **SimpleProject** 資料夾名為 `SimpleProjectFactory.cs`。  
  
4.  新增下列 using 陳述式︰  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  將 Guid 屬性加入至 SimpleProjectFactory 類別。 屬性的值會是新的專案 factory 的 GUID。  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 現在您可以註冊您的專案範本。  
  
#### 若要註冊的專案範本  
  
1.  在 SimpleProjectPackage.cs，加入 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 屬性 SimpleProjectPackage 類別，如下所示。  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  重建方案並確認它建置無誤。  
  
     重建登錄專案範本。  
  
 參數 `defaultProjectExtension` 和 `possibleProjectExtensions` 設專案檔案的副檔名 \(.myproj\)。`projectTemplatesDirectory` 參數設定為 \[範本\] 資料夾的相對路徑。 建置期間，此路徑會轉換成完整建置，並加入至登錄，以註冊專案系統。  
  
## 測試範本註冊  
 範本註冊會告知 Visual Studio 專案範本資料夾的位置，讓 Visual Studio 可以顯示的範本名稱和圖示 **新的專案** 對話方塊。  
  
#### 若要測試範本註冊  
  
1.  按 F5 開始偵錯的 Visual Studio 的實驗執行個體。  
  
2.  在實驗執行個體中，建立您剛建立的專案類型的新專案。 在 **新的專案** 對話方塊中，您應該會看到 **SimpleProject** 下 **已安裝的範本**。  
  
 現在您已註冊的專案處理站。 不過，它還無法建立專案。 專案封裝和專案工廠一起建立和初始化專案。  
  
## 新增管理封裝架構程式碼  
 實作專案封裝和專案 factory 之間的連線。  
  
-   匯入管理套件架構的原始程式碼檔。  
  
    1.  卸載 SimpleProject 專案 \(在 **方案總管\] 中**, ，選取專案節點，然後在內容功能表上按一下 \[ **卸載專案**。\) 和 XML 編輯器中開啟專案檔案。  
  
    2.  將下列區塊加入至專案檔 （正上方的 \< 匯入 \> 區塊）。 ProjectBasePath 設 ProjectBase.files 檔案，在您剛才下載的管理套件架構程式碼中的位置。 您可能必須加入一個反斜線的路徑名稱。 如果不這麼做，可能無法找到管理套件 Framework 程式碼專案。  
  
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
  
        -   Microsoft.VisualStudio.Designer.Interfaces （在 \< VSSDK 安裝 \> \\VisualStudioIntegration\\Common\\Assemblies\\v2.0\)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### 用於初始化專案處理站  
  
1.  在 SimpleProjectPackage.cs 檔案中，新增下列 `using` 陳述式。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  衍生 `SimpleProjectPackage` 類別是從 `Microsoft.VisualStudio.Package.ProjectPackage`。  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  登錄專案中心。 將下列行加入 `SimpleProjectPackage.Initialize` 方法中，正後方 `base.Initialize`。  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  實作抽象屬性 `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  在 SimpleProjectFactory.cs，新增下列 `using` 陳述式，在現有 `using` 陳述式。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  衍生 `SimpleProjectFactory` 類別是從 `ProjectFactory`。  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  新增下列虛擬方法，以 `SimpleProjectFactory` 類別。 您將在稍後的章節中實作這個方法。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  將下列欄位和建構函式來新增 `SimpleProjectFactory` 類別。 這 `SimpleProjectPackage` 參考快取在私用欄位，讓它可用於設定服務提供者站台。  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. 重建方案並確認它建置無誤。  
  
## 測試專案的處理站實作  
 測試是否您專案的處理站實作的建構函式呼叫。  
  
#### 若要測試專案處理站的實作  
  
1.  在 SimpleProjectFactory.cs 檔案中，設定中斷點在下一行 `SimpleProjectFactory` 建構函式。  
  
    ```  
    this.package = package;  
    ```  
  
2.  按 f5 鍵啟動 Visual studio 的實驗執行個體。  
  
3.  在實驗性的執行個體，開始建立新的專案。在 **新的專案** 對話方塊中，選取 SimpleProject 專案類型，然後按一下 **確定**。 執行會在中斷點停止。  
  
4.  清除中斷點，然後停止偵錯。 因為我們還沒有建立的專案節點，則專案建立程式碼仍然擲回例外狀況。  
  
## 擴充專案節點類別  
 現在，您可以實作 `SimpleProjectNode` 類別，衍生自 `ProjectNode` 類別。`ProjectNode` 基底類別會處理建立專案的下列工作︰  
  
-   將專案範本檔案，SimpleProject.myproj，複製到新的專案資料夾。 複本會根據輸入的名稱重新命名 **新的專案** 對話方塊。`ProjectGuid` 屬性值會取代新的 GUID。  
  
-   周遊的專案範本檔案，SimpleProject.myproj，MSBuild 項目，並尋找 `Compile` 項目。 每個 `Compile` 目標檔案，將檔案複製到新的專案資料夾。  
  
 衍生 `SimpleProjectNode` 類別會處理這些工作︰  
  
-   可讓專案和檔案中的節點圖示 **方案總管\] 中** 要建立或選取。  
  
-   可讓其他專案範本參數替代項目來指定。  
  
#### 若要擴充專案節點類別  
  
1.  
  
2.  新增名為 `SimpleProjectNode.cs`。  
  
3.  下列程式碼取代現有的程式碼。  
  
    ```  
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
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
 這 `SimpleProjectNode` 類別實作有這些覆寫的方法︰  
  
-   `ProjectGuid`, 它會傳回專案 factory 的 GUID。  
  
-   `ProjectType`, 它會傳回該專案類型的當地語系化的名稱。  
  
-   `AddFileFromTemplate`, 這將選取的檔案從 \[範本\] 資料夾複製到目的專案。 在稍後的章節進一步實作這個方法。  
  
 `SimpleProjectNode` 建構函式一樣 `SimpleProjectFactory` 建構函式，會快取 `SimpleProjectPackage` 中供稍後使用的私用欄位的參考。  
  
 連接 `SimpleProjectFactory` 類別 `SimpleProjectNode` 類別中，您必須具現化新 `SimpleProjectNode` 中 `SimpleProjectFactory.CreateProject` 方法並加以快取中供稍後使用的私用欄位。  
  
#### 連接專案 factory 類別和節點類別  
  
1.  在 SimpleProjectFactory.cs 檔案中，新增下列 `using` 陳述式︰  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  取代 `SimpleProjectFactory.CreateProject` 方法藉由使用下列程式碼。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  重建方案並確認它建置無誤。  
  
## 測試專案節點類別  
 測試您的專案 factory，以查看它是否會建立專案階層架構。  
  
#### 若要測試專案節點類別  
  
1.  按 F5 鍵啟動偵錯作業。 在實驗執行個體中，建立新的 SimpleProject。  
  
2.  Visual Studio 應該呼叫您的專案建立專案。  
  
3.  關閉 Visual Studio 的實驗執行個體。  
  
## 加入自訂的專案節點圖示  
 在前一節中的 \[專案\] 節點圖示是預設圖示。 您可以將它變更自訂圖示。  
  
#### 若要加入自訂的專案節點圖示  
  
1.  在 **資源** 資料夾中，新增名為 SimpleProjectNode.bmp 的點陣圖檔案。  
  
2.  在 **屬性** windows，減少為 16 x 16 像素的點陣圖。 請特殊的點陣圖。  
  
     ![簡單專案 Comm](~/extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  在 **屬性** \] 視窗中，變更 **建置動作** 點陣圖來 **內嵌資源**。  
  
4.  在 SimpleProjectNode.cs，新增下列 `using` 陳述式︰  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  將下列靜態欄位和建構函式來加入 `SimpleProjectNode` 類別。  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  將下列屬性加入開頭 `SimpleProjectNode` 類別。  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  取代下列程式碼的執行個體建構函式。  
  
    ```  
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
  
 靜態在建構期間， `SimpleProjectNode` 擷取組件資訊清單資源的專案節點點陣圖和快取在私用欄位，以供稍後使用。 請注意語法 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 影像路徑。 若要查看的資訊清單資源內嵌在組件名稱，請使用 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 方法。 當這個方法會套用至 `SimpleProject` ，結果應該將組件，如下所示︰  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 在執行個體建構期間 `ProjectNode` 基底類別載入的 Resources.imagelis.bmp，其中都是從 Resources\\imagelis.bmp 內嵌常用的 16x16 點陣圖。 此點陣圖清單開放給 `SimpleProjectNode` 為 ImageHandler.ImageList。`SimpleProjectNode` 將專案節點點陣圖附加至清單。 專案節點點陣圖影像清單中的位移會快取供稍後使用，做為公用值 `ImageIndex` 屬性。 Visual Studio 會使用這個屬性來決定要顯示為 \[專案\] 節點圖示的點陣圖。  
  
## 測試自訂專案節點圖示  
 測試您的專案 factory，以查看它是否會建立具有您自訂專案的節點圖示專案階層架構。  
  
#### 若要測試自訂專案節點圖示  
  
1.  開始偵錯，並在實驗執行個體中建立新的 SimpleProject。  
  
2.  在剛建立的專案，請注意 SimpleProjectNode.bmp 當做專案節點圖示。  
  
     ![簡單專案新增專案節點](~/extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  程式碼編輯器中開啟 Program.cs。 您應該會看到類似下列的程式碼的原始程式碼。  
  
    ```  
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
  
     請注意，範本參數 $nameSpace$ 和 $className$ 沒有新的值。 您將學習如何實作下一節中的範本參數替代。  
  
## 取代範本參數  
 在先前章節中，您的專案範本與 Visual Studio 使用註冊 `ProvideProjectFactory` 屬性。 註冊範本資料夾的路徑，以這種方式可讓您覆寫，並展開啟用基本的範本參數替代 `ProjectNode.AddFileFromTemplate` 類別。 如需詳細資訊，請參閱[新產生的專案: 在幕後，第二部](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)。  
  
 現在加入取代程式碼，以 `AddFileFromTemplate` 類別。  
  
#### 取代範本參數  
  
1.  在 SimpleProjectNode.cs 檔案中，新增下列 `using` 陳述式。  
  
    ```  
    using System.IO;  
    ```  
  
2.  取代 `AddFileFromTemplate` 方法藉由使用下列程式碼。  
  
    ```  
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
  
3.  只要之後設定一個中斷點，在方法中， `className` 指派陳述式。  
  
 指派陳述式決定命名空間和新的類別名稱的合理值。 這兩個 `ProjectNode.FileTemplateProcessor.AddReplace` 方法呼叫使用這些新值取代對應的範本參數值。  
  
## 測試範本參數替代  
 現在，您可以測試範本參數替代。  
  
#### 若要測試的範本參數替代作業  
  
1.  開始偵錯，並在實驗執行個體中建立新的 SimpleProject。  
  
2.  在中斷點停止執行 `AddFileFromTemplate` 方法。  
  
3.  檢查值 `nameSpace` 和 `className` 參數。  
  
    -   `nameSpace` 值會指定在 \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj 專案範本檔案的 \< RootNamespace \> 項目。 在此情況下，值為"MyRootNamespace"。  
  
    -   `className` 值會指定類別的來源檔案名稱，而不需要檔案的副檔名。 在此案例中，第一個檔案複製到目的地資料夾是 AssemblyInfo.cs;因此，類別名稱的值是 「 AssemblyInfo 」。  
  
4.  移除中斷點，然後按 f5 鍵繼續執行。  
  
     Visual Studio 應該完成建立專案。  
  
5.  程式碼編輯器中開啟 Program.cs。 您應該會看到類似下列的程式碼的原始程式碼。  
  
    ```  
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
  
     請注意，命名空間現在是"MyRootNamespace"和類別名稱現在是 「 程式 」。  
  
6.  開始偵錯專案。 新的專案應該編譯、 執行和顯示"Hello VSX"\!\!\! 在主控台視窗。  
  
     ![簡單專案命令](~/extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 恭喜您！ 您已實作的基本管理的專案系統。