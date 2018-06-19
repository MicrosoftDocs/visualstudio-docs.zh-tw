---
title: 建立基本專案系統，第 1 部分 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ceb7bb63caf3677c3758d88713308daa0c34fb4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108332"
---
# <a name="creating-a-basic-project-system-part-1"></a>建立基本專案系統，第 1 部分
在 Visual Studio 專案是開發人員用來組織原始程式碼檔和其他資產的容器。 專案會顯示為子系中的解決方案**方案總管 中**。 專案可讓您組織、 建置、 偵錯和部署來源的程式碼並建立 Web 服務、 資料庫和其他資源的參考。  
  
 專案檔案中定義的專案，例如 Visual C# 專案.csproj 檔案。 您可以建立您自己有自己的專案副檔名的專案類型。 如需專案類型的詳細資訊，請參閱[專案類型](../extensibility/internals/project-types.md)。  
  
> [!NOTE]
>  如果您需要自訂專案類型擴充 Visual Studio，我們強烈建議利用[Visual Studio 專案系統](https://github.com/Microsoft/VSProjectSystem)(VSPS) 具有許多優於建置從頭專案系統：  
>   
>  -  簡單的入門訓練。  即使基本專案系統會要求數以萬計的程式碼行。  利用 VSPS 可上架成本減少按幾下之前您準備好要自訂您的需求。  
>  -  更容易維護。  利用 VSPS，您只需要維護您自己的案例。  我們會處理所有的專案系統基礎結構的保養。  
>   
>  如果您需要早於 Visual Studio 2013 的 Visual Studio 目標版本，您無法在 Visual Studio 擴充功能中利用 VSPS。  如果是這樣，這個逐步解說是很好的起點開始。  
  
 本逐步解說將示範如何建立具有專案檔案名稱副檔名.myproj 專案類型。 本逐步解說借用從現有的 Visual C# 專案系統。  
  
> [!NOTE]
>  擴充專案的其他範例，請參閱[VSSDK 範例](http://aka.ms/vs2015sdksamples)。  
  
 本逐步解說教導如何完成這些工作：  
  
-   建立基本專案類型。  
  
-   建立基本專案範本。  
  
-   註冊 Visual Studio 專案範本。  
  
-   建立專案的執行個體開啟**新專案**對話方塊，然後使用您的範本。  
  
-   建立您的專案系統的專案處理站。  
  
-   建立您的專案系統的專案節點。  
  
-   新增自訂專案系統的圖示。  
  
-   實作基本的範本參數替代。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 您也必須下載的程式碼[專案的 Managed Package Framework](http://mpfproj12.codeplex.com/)。 將檔案解壓縮至可以存取您要建立的方案的位置。  
  
## <a name="creating-a-basic-project-type"></a>建立基本專案類型  
 C# VSIX 專案建立一個名為**SimpleProject**。 (**新檔案、 專案**然後**Visual C# 擴充性 VSIX 專案**)。 加入 Visual Studio Package 專案項目範本 (在 [方案總管] 中，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**，然後移至**擴充性 / Visual Studio Package**)。 將檔案命名**SimpleProjectPackage**。  
  
## <a name="creating-a-basic-project-template"></a>建立基本專案範本  
 現在，您可以修改此基本的 VSPackage 實作新的.myproj 專案類型。 若要建立.myproj 專案類型為基礎的專案，Visual Studio 必須知道哪些檔案、 資源和新的專案中加入的參考。 若要提供這項資訊，專案將檔案放在專案範本資料夾。 當使用者使用.myproj 專案建立專案時，檔案會複製到新的專案。  
  
#### <a name="to-create-a-basic-project-template"></a>若要建立基本專案範本  
  
1.  將三個資料夾加入至專案，在 [其他] 其中一個： **Templates\Projects\SimpleProject**。 (在**方案總管] 中**，以滑鼠右鍵按一下**SimpleProject**專案節點，指向**新增**，然後按一下 [**新資料夾**。 將資料夾命名為 `Templates`註冊免費試用帳戶。 在**範本**資料夾中，加入名為的資料夾`Projects`。 在**專案**資料夾中，加入名為的資料夾`SimpleProject`。)  
  
2.  在**Templates\Projects\SimpleProject**資料夾中，加入要使用名為圖示的點陣圖影像檔案`SimpleProject.ico`。 當您按一下**新增**，圖示編輯器 隨即開啟。  
  
3.  請特殊圖示。 此圖示會出現在**新專案**稍後在本逐步解說中的對話方塊。  
  
     ![簡單專案圖示](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  儲存圖示並關閉圖示編輯器。  
  
5.  在**Templates\Projects\SimpleProject**資料夾中，加入**類別**項目的名稱`Program.cs`。  
  
6.  現有的程式碼取代下列幾行。  
  
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
    >  這不是最終形式 Program.cs 程式碼;取代參數會在稍後步驟中處理。 您可能會看到編譯錯誤，但只要檔案**BuildAction**是**內容**，您應該能夠建置並如往常般執行專案。  
  
1.  儲存檔案。  
  
2.  AssemblyInfo.cs 檔案複製**屬性**資料夾**Projects\SimpleProject**資料夾。  
  
3.  在**Projects\SimpleProject**資料夾加入名為 XML 檔案`SimpleProject.myproj`。  
  
    > [!NOTE]
    >  此類型的所有專案的副檔名是.myproj。 如果您想要變更它，您必須變更它被提及的逐步解說中的每個地方。  
  
4.  現有的內容取代為下列幾行。  
  
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
  
6.  在**屬性**視窗中，將**建置動作**AssemblyInfo.cs、 Program.cs、 SimpleProject.ico，和以 SimpleProject.myproj**內容**，並設定其**在 VSIX 中包含**屬性**True**。  
  
 這個專案範本會描述基本 Visual C# 專案的偵錯組態和發行組態。 專案包含兩個原始程式檔、 AssemblyInfo.cs、 Program.cs，以及數個組件的參考。 從範本建立專案時，ProjectGuid 值會自動取代新的 GUID。  
  
 在**方案總管 中**，展開**範本**資料夾應該會出現，如下所示：

```
Templates  
   Projects  
      SimpleProject  
         AssemblyInfo.cs  
         Program.cs  
         SimpleProject.ico  
         SimpleProject.myproj  
```

## <a name="creating-a-basic-project-factory"></a>建立基本專案 Factory  
 您必須告訴 Visual Studio 專案範本資料夾的位置。 若要這樣做，請將屬性加入實作 project factory，以便建置 VSPackage 時，將會寫入至系統登錄的範本位置的 VSPackage 類別。 開始建立專案的 factory GUID 所識別的基本專案 factory。 使用<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>連接 project factory SimpleProjectPackage 類別的屬性。  
  
#### <a name="to-create-a-basic-project-factory"></a>若要建立基本專案 factory  
  
1.  建立專案 factory 的 Guid (上**工具**功能表上，按一下 **建立 GUID**)，或使用下列範例中的一個。 含有已定義的區段附近 SimpleProjectPackage 類別中加入 Guid `PackageGuidString`。 GUID 表單和字串格式必須是 Guid。 產生的程式碼應該類似下列的範例。  
  
    ```csharp  
        public sealed class SimpleProjectPackage : Package
        {  
            ...
            public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
            public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
    
            public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);  
        }  
    ```  
  
3.  將類別加入頂端**SimpleProject**資料夾名為`SimpleProjectFactory.cs`。  
  
4.  加入下列 using 陳述式：  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  加入 SimpleProjectFactory 類別 Guid 屬性。 屬性的值是新的 project factory 的 GUID。  
  
    ```csharp  
    [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 現在您可以註冊您的專案範本。  
  
#### <a name="to-register-the-project-template"></a>若要註冊的專案範本  
  
1.  在 SimpleProjectPackage.cs，加入<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>屬性 SimpleProjectPackage 類別，如下所示。  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectPackage.PackageGuidString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  重建方案，並確認它建置無誤。  
  
     重建登錄專案範本。  
  
 參數`defaultProjectExtension`和`possibleProjectExtensions`會設定為專案檔案的副檔名 (.myproj)。 `projectTemplatesDirectory`參數設定為 [範本] 資料夾的相對路徑。 建置期間，此路徑會轉換成完整建置，新增至登錄，以註冊專案系統。  
  
## <a name="testing-the-template-registration"></a>測試範本註冊  
 範本註冊會告知 Visual Studio 專案範本資料夾的位置，讓 Visual Studio 可以顯示的範本名稱和圖示**新專案** 對話方塊。  
  
#### <a name="to-test-the-template-registration"></a>若要測試範本註冊  
  
1.  按 f5 鍵啟動偵錯 Visual studio 的實驗執行個體。  
  
2.  在實驗執行個體，建立新的專案，您剛建立的專案類型。 在**新專案**對話方塊中，您應該會看到**SimpleProject**下**安裝的範本**。  
  
 現在您有已註冊的 project factory。 不過，它還無法建立專案。 專案封裝和專案 factory 一起建立和初始化專案。  
  
## <a name="add-the-managed-package-framework-code"></a>將 Managed Package Framework 程式碼  
 實作專案封裝與專案 factory 之間的連線。  
  
-   Managed 封裝架構匯入的原始程式碼檔案。  
  
    1.  卸載 SimpleProject 專案 (在**方案總管 中**，選取專案節點，然後在內容功能表上按一下**卸載專案**。) 和 XML 編輯器中開啟專案檔。  
  
    2.  將下列區塊加入至專案檔 (正上方\<匯入 > 區塊)。 ProjectBasePath 設 ProjectBase.files 檔案，在您剛才下載的 Managed Package Framework 程式碼中的位置。 您可能必須加入反斜線的路徑名稱。 如果不這麼做，專案可能無法找到 Managed Package Framework 程式碼。  
  
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
  
        -   Microsoft.VisualStudio.Designer.Interfaces (在\<VSSDK 安裝 > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>初始化 project factory  
  
1.  在 SimpleProjectPackage.cs 檔案中，加入下列`using`陳述式。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  衍生`SimpleProjectPackage`類別從`Microsoft.VisualStudio.Package.ProjectPackage`。  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  註冊 project factory。 將下列行加入`SimpleProjectPackage.Initialize`方法，就在`base.Initialize`。  
  
    ```  
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
  
5.  在 SimpleProjectFactory.cs，加入下列`using`陳述式後方`using`陳述式。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  衍生`SimpleProjectFactory`類別從`ProjectFactory`。  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  將下列的虛擬方法，加入`SimpleProjectFactory`類別。 後面的章節中，您會實作這個方法。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  將下列欄位和建構函式來加入`SimpleProjectFactory`類別。 這`SimpleProjectPackage`參考會快取中的私用欄位，使其可以用在設定服務提供者站台。  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. 重建方案，並確認它建置無誤。  
  
## <a name="testing-the-project-factory-implementation"></a>測試 Project Factory 實作  
 測試是否會呼叫您 project factory 實作的建構函式。  
  
#### <a name="to-test-the-project-factory-implementation"></a>若要測試 project factory 實作  
  
1.  在 SimpleProjectFactory.cs 檔案中，請在下一行中設定中斷點`SimpleProjectFactory`建構函式。  
  
    ```  
    this.package = package;  
    ```  
  
2.  按 f5 鍵啟動 Visual studio 的實驗執行個體。  
  
3.  在實驗性執行個體中，開始建立新的專案。在**新專案**對話方塊中，選取 SimpleProject 專案類型，然後按一下**確定**。 執行會在中斷點停止。  
  
4.  清除中斷點，然後停止偵錯。 由於我們有尚未建立的專案節點，則專案建立程式碼仍然擲回例外狀況。  
  
## <a name="extending-the-project-node-class"></a>擴充專案節點類別  
 現在您可以實作`SimpleProjectNode`類別，衍生自`ProjectNode`類別。 `ProjectNode`基底類別處理的專案建立下列工作：  
  
-   將專案範本檔 SimpleProject.myproj，複製到新的專案資料夾。 根據輸入中的名稱重新命名複製**新專案** 對話方塊。 `ProjectGuid`屬性值會取代為新的 GUID。  
  
-   周遊專案範本檔 SimpleProject.myproj，MSBuild 項目，並尋找`Compile`項目。 每個`Compile`目標檔案，將檔案複製到新的專案資料夾。  
  
 在衍生`SimpleProjectNode`類別會處理這些工作：  
  
-   可讓專案和檔案中的節點圖示**方案總管 中**来建立或選取。  
  
-   啟用要指定其他專案範本參數替代。  
  
#### <a name="to-extend-the-project-node-class"></a>若要擴充的專案節點類別  
  
1.  
  
2.  將類別命名為`SimpleProjectNode.cs`。  
  
3.  將現有的程式碼取代為下列程式碼。  
  
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
  
 這`SimpleProjectNode`類別實作會有這些覆寫的方法：  
  
-   `ProjectGuid`它會傳回 project factory 的 GUID。  
  
-   `ProjectType`它會傳回該專案類型的當地語系化的名稱。  
  
-   `AddFileFromTemplate`其中將選取的檔案從範本資料夾複製到目的地專案。 在稍後的章節進一步實作這個方法。  
  
 `SimpleProjectNode`建構函式、 like`SimpleProjectFactory`建構函式，會快取`SimpleProjectPackage`中供稍後使用的私用欄位的參考。  
  
 連接`SimpleProjectFactory`類別`SimpleProjectNode`類別，您必須具現化新`SimpleProjectNode`中`SimpleProjectFactory.CreateProject`方法並加以快取中供稍後使用的私用欄位。  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>若要連接的專案 factory 類別與節點類別  
  
1.  在 SimpleProjectFactory.cs 檔案中，加入下列`using`陳述式：  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  取代`SimpleProjectFactory.CreateProject`方法藉由使用下列程式碼。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  重建方案，並確認它建置無誤。  
  
## <a name="testing-the-project-node-class"></a>測試專案節點類別  
 測試您的專案 factory，以查看它是否會建立專案階層架構。  
  
#### <a name="to-test-the-project-node-class"></a>若要測試的專案節點類別  
  
1.  按 F5 鍵啟動偵錯作業。 在實驗執行個體，建立新的 SimpleProject。  
  
2.  Visual Studio 應該呼叫您專案的 factory 來建立專案。  
  
3.  關閉 Visual Studio 的實驗執行個體。  
  
## <a name="adding-a-custom-project-node-icon"></a>加入自訂專案節點圖示  
 在前一節中的專案節點圖示是預設的圖示。 您可以將它變更為自訂圖示。  
  
#### <a name="to-add-a-custom-project-node-icon"></a>若要加入自訂專案節點圖示  
  
1.  在**資源**資料夾中，加入名為 SimpleProjectNode.bmp 的點陣圖檔案。  
  
2.  在**屬性**windows，降低為 16 x 16 像素的點陣圖。 請特殊點陣圖。  
  
     ![簡單專案 Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  在**屬性**視窗中，變更**建置動作**點陣圖來**內嵌資源**。  
  
4.  在 SimpleProjectNode.cs，加入下列`using`陳述式：  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  加入下列的靜態欄位和建構函式來`SimpleProjectNode`類別。  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  將下列屬性加入開頭`SimpleProjectNode`類別。  
  
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
  
 靜態建構期間`SimpleProjectNode`擷取組件資訊清單資源的專案節點點陣圖並快取中供稍後使用的私用欄位。 請注意的語法<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>映像路徑。 若要查看的組件中內嵌的資訊清單資源名稱，請使用<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>方法。 當這個方法會套用到`SimpleProject`組件的結果應該如下：  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 在執行個體建構期間`ProjectNode`基底類別載入的 Resources.imagelis.bmp，其中都是從 Resources\imagelis.bmp 內嵌常用的 16 x 16 點陣圖。 此點陣圖清單開放給`SimpleProjectNode`ImageHandler.ImageList 為。 `SimpleProjectNode` 將專案節點點陣圖附加至清單。 專案節點點陣圖影像清單中的位移會快取供稍後使用，做為公用值`ImageIndex`屬性。 Visual Studio 會使用這個屬性來決定要顯示為專案節點圖示的點陣圖。  
  
## <a name="testing-the-custom-project-node-icon"></a>測試自訂專案節點圖示  
 測試您的專案 factory，以查看它是否會建立您的自訂專案節點圖示的專案階層。  
  
#### <a name="to-test-the-custom-project-node-icon"></a>若要測試自訂專案節點圖示  
  
1.  開始偵錯，並在實驗執行個體中建立新的 SimpleProject。  
  
2.  在新建的專案中，請注意 SimpleProjectNode.bmp 當做專案節點圖示。  
  
     ![簡單專案新增專案節點](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  程式碼編輯器中開啟 Program.cs。 您應該會看到類似下列程式碼的原始程式碼。  
  
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
  
     請注意，範本參數 $nameSpace$ 和 $className$ 不需要新的值。 您將學習如何實作下一節中的範本參數替代。  
  
## <a name="substituting-template-parameters"></a>取代範本參數  
 在先前章節中，您的專案範本使用 Visual Studio 註冊使用`ProvideProjectFactory`屬性。 註冊範本資料夾的路徑以這種方式可讓您藉由覆寫，並展開啟用基本的範本參數替代`ProjectNode.AddFileFromTemplate`類別。 如需詳細資訊，請參閱[產生新的專案： 在其實、 第二部分](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。  
  
 現在將 取代程式碼加入`AddFileFromTemplate`類別。  
  
#### <a name="to-substitute-template-parameters"></a>若要取代範本參數  
  
1.  在 SimpleProjectNode.cs 檔案中，加入下列`using`陳述式。  
  
    ```  
    using System.IO;  
    ```  
  
2.  取代`AddFileFromTemplate`方法藉由使用下列程式碼。  
  
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
  
3.  設定在方法中，中斷點後方`className`指派陳述式。  
  
 指派陳述式決定命名空間和新的類別名稱的合理值。 這兩個`ProjectNode.FileTemplateProcessor.AddReplace`方法會呼叫使用這些新值取代對應的範本參數值。  
  
## <a name="testing-the-template-parameter-substitution"></a>測試範本參數替代  
 現在您可以測試範本參數替代。  
  
#### <a name="to-test-the-template-parameter-substitution"></a>若要測試的範本參數替代  
  
1.  開始偵錯，並在實驗執行個體中建立新的 SimpleProject。  
  
2.  中的中斷點處停止執行`AddFileFromTemplate`方法。  
  
3.  檢查的值`nameSpace`和`className`參數。  
  
    -   `nameSpace` 指定的值\<RootNamespace > \Templates\Projects\SimpleProject\SimpleProject.myproj 專案範本檔案中的項目。 在此情況下，值為"MyRootNamespace"。  
  
    -   `className` 提供類別的來源檔案名稱，不含副檔名名稱的值。 在此情況下，第一個檔案複製到目的資料夾是 AssemblyInfo.cs;因此，類別名稱的值是"AssemblyInfo"。  
  
4.  移除中斷點，然後按 f5 鍵繼續執行。  
  
     Visual Studio 應完成建立專案。  
  
5.  程式碼編輯器中開啟 Program.cs。 您應該會看到類似下列程式碼的原始程式碼。  
  
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
  
6.  開始偵錯專案。 新的專案應該編譯、 執行和顯示"Hello VSX"!!! 。  
  
     ![簡單專案命令](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 恭喜您！ 您已實作的基本受管理的專案系統。