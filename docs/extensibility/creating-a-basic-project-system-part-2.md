---
title: "建立基本專案系統，第 2 部分 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9b3f46a0e4fb87e6064fb3e975cd6b7313270c13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-basic-project-system-part-2"></a>建立基本專案系統，第 2 部分
在這一系列，第一個逐步解說[建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)，示範如何建立基本專案系統。 本逐步解說為基礎的基本專案系統所加入 Visual Studio 範本、 屬性頁，以及其他功能。 您必須先完成第一個逐步解說，才能啟動這一個。  
  
 本逐步解說教導如何建立具有專案檔案名稱副檔名.myproj 專案類型。 若要完成此逐步解說，您不必建立您自己的語言，因為現有的 Visual C# 專案系統借用的逐步解說。  
  
 本逐步解說教導如何完成這些工作：  
  
-   建立 Visual Studio 範本。  
  
-   部署 Visual Studio 範本。  
  
-   建立專案類型子節點中的**新專案** 對話方塊。  
  
-   啟用在 Visual Studio 範本參數替代。  
  
-   建立在專案屬性頁。  
  
> [!NOTE]
>  在本逐步解說的步驟以 C# 專案。 不過，除了副檔名的檔案和程式碼等特性，您可以使用相同的步驟 Visual Basic 專案。  
  
## <a name="creating-a-visual-studio-template"></a>建立 Visual Studio 範本  
 [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)示範如何建立基本專案範本，並將它加入至專案系統。 它也示範如何使用此範本註冊使用 Visual Studio<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>屬性，在系統登錄中寫入 \Templates\Projects\SimpleProject\ 資料夾的完整路徑。  
  
 藉由使用 Visual Studio 範本 （.vstemplate 檔案），而不基本的專案範本，您可以控制的範本顯示於**新專案**對話方塊和如何取代範本參數。  這個.vstemplate 檔案會描述如何使用專案系統範本建立專案時要包含的來源檔案的 XML 檔案。 專案系統本身所收集的.vstemplate 檔和原始程式檔在.zip 檔案，建置並部署至 Visual Studio 已知的位置複製.zip 檔案。 稍後在本逐步解說將詳細說明此程序。  
  
1.  在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，開啟您依照建立的 SimpleProject 方案[建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)。  
  
2.  在 SimpleProjectPackage.cs 檔案中，尋找 ProvideProjectFactory 屬性。 取代 null，第二個參數 （專案名稱） 和第四個參數 （在專案範本資料夾的路徑） 」。\\\NullPath"、，如下所示。  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
        ".\\NullPath",  
    LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  加入名為 SimpleProject.vstemplate \Templates\Projects\SimpleProject\ 資料夾到 XML 檔案。  
  
4.  SimpleProject.vstemplate 的內容取代為下列程式碼。  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
      <TemplateData>  
        <Name>SimpleProject Application</Name>  
        <Description>  
            A project for creating a SimpleProject application  
         </Description>  
         <Icon>SimpleProject.ico</Icon>  
         <ProjectType>SimpleProject</ProjectType>  
      </TemplateData>  
      <TemplateContent>  
        <Project File="SimpleProject.myproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
              Program.cs  
          </ProjectItem>  
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
             AssemblyInfo.cs  
          </ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
5.  在**屬性**視窗中，選取所有五個檔案的 \Templates\Projects\SimpleProject\ 資料夾，以及組**建置動作**至**ZipProject**。  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 \<TemplateData > 一節決定 SimpleProject 專案類型中的外觀與位置**新專案**對話方塊，如下所示：  
  
-   \<名稱 > 項目名稱 SimpleProject 的應用程式的專案範本。  
  
-   \<描述 > 項目包含會出現在描述**新專案**對話方塊中選取專案範本時。  
  
-   \<圖示 > 項目會指定出現 SimpleProject 專案類型的圖示。  
  
-   \<ProjectType > 項目名稱中的專案類型**新專案** 對話方塊。 這個名稱會取代 ProvideProjectFactory 屬性的專案名稱參數。  
  
    > [!NOTE]
    >  \<ProjectType > 項目必須符合`LanguageVsTemplate`引數的`ProvideProjectFactory`SimpleProjectPackage.cs 檔案中的屬性。  
  
 \<TemplateContent > 一節將說明這些新的專案建立時產生的檔案：  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 這三個檔案有`ReplaceParameters`設為 true，可讓參數替代。  在 Program.cs 檔案中有`OpenInEditor`設為 true，這會導致要建立專案時，程式碼編輯器中開啟的檔案。  
  
 如需 Visual Studio 範本結構描述中元素的詳細資訊，請參閱[Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
> [!NOTE]
>  如果專案具有多個 Visual Studio 範本，每一個範本是在個別的資料夾。 該資料夾中的每個檔案必須具有**建置動作**設**ZipProject**。  
  
## <a name="adding-a-minimal-vsct-file"></a>若要加入最小.vsct 檔案  
 Visual Studio 必須以辨識新的或修改 Visual Studio 範本的安裝模式執行。 安裝模式需要必須存在.vsct 檔案。 因此，您必須將最小.vsct 檔案加入專案。  
  
1.  新增名 SimpleProject.vsct SimpleProject 專案的 XML 檔案。  
  
2.  SimpleProject.vsct 檔案的內容取代為下列程式碼。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  設定**建置動作**到這個檔案的**VSCTCompile**。 您可以只在.csproj 檔案中，無法顯示於**屬性**視窗。 請確定**建置動作**這個檔案設**無**此時。  
  
    1.  以滑鼠右鍵按一下 SimpleProject 節點，然後按一下**編輯 SimpleProject.csproj**。  
  
    2.  在.csproj 檔案中，找出 SimpleProject.vsct 項目。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  變更的建置動作**VSCTCompile**。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  專案檔及關閉編輯器。  
  
    5.  儲存 SimpleProject 節點，然後在**方案總管 中**按一下**重新載入專案**。  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>檢查 Visual Studio 範本建置步驟  
 VSPackage 專案的建置系統一般而言 Visual Studio 中設定模式時執行的.vstemplate 檔已變更，或包含.vstemplate 檔案的專案就會重建。 您可以展開冒險藉由設定為 Normal 或更高版本的 MSBuild 的詳細資訊層級。  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  展開**專案和方案**節點，然後再選取**建置並執行**。  
  
3.  設定**MSBuild 專案組建輸出詳細等級**至**一般**。 按一下 [確定 **Deploying Office Solutions**]。  
  
4.  重建 SimpleProject 專案。  
  
 建置步驟來建立.zip 專案檔應該類似下列的範例。  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>部署 Visual Studio 範本  
 Visual Studio 範本不包含路徑資訊。 因此，範本的.zip 檔案必須部署至 Visual Studio 已知的位置。 ProjectTemplates 資料夾的位置通常是 **\<%LOCALAPPDATA%> \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**。  
  
 若要部署您的專案 factory，安裝程式必須具有系統管理員權限。 部署 Visual Studio 安裝 節點下的 範本： **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**。  
  
## <a name="testing-a-visual-studio-template"></a>測試 Visual Studio 範本  
 測試您的專案 factory，以查看是否使用 Visual Studio 範本建立專案階層架構。  
  
1.  重設 Visual Studio SDK 的實驗執行個體。  
  
     在[!INCLUDE[win7](../debugger/includes/win7_md.md)]： 在 [開始] 功能表上尋找**Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools**資料夾，然後再選取**重設 Microsoft Visual Studio 實驗執行個體**。  
  
     Windows 的更新版本上： 在 [開始] 畫面中，輸入**重設 Microsoft Visual Studio\<版本 > 實驗執行個體**。  
  
2.  命令提示字元 視窗隨即出現。 您會看到字樣`Press any key to continue`，按 ENTER。 在視窗關閉後，開啟 Visual Studio。  
  
3.  重建 SimpleProject 專案並開始偵錯。 實驗執行個體隨即出現。  
  
4.  在實驗執行個體，建立 SimpleProject 專案。 在**新專案**對話方塊中，選取**SimpleProject**。  
  
5.  您應該會看到 SimpleProject 的新執行個體。  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>建立專案類型的子節點  
 您可以加入中的專案類型節點的子節點**新專案** 對話方塊。  例如，針對 SimpleProject 專案類型中，您可能會的主控台應用程式、 視窗的應用程式、 web 應用程式，以及其他子節點。  
  
 建立子節點會變更專案檔，並將\<OutputSubPath > 的子系\<ZipProject > 項目。 複製範本時，在建置或部署期間，每一個子節點會成為專案範本資料夾的子資料夾。  
  
 本節說明如何建立主控台子節點 SimpleProject 專案類型。  
  
1.  將 \Templates\Projects\SimpleProject\ 資料夾重新命名 \Templates\Projects\ConsoleApp\\。  
  
2.  在**屬性**視窗中，選取 \Templates\Projects\ConsoleApp\ 資料夾中的所有五個檔案，並確定**建置動作**設**ZipProject**。  
  
3.  在 SimpleProject.vstemplate 檔案中，加入下列行結尾處\<TemplateData > 區段中的，在結束標記之前。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     這會導致出現在主控台的子節點和 SimpleProject 父節點，也就是一層的子節點中的主控台應用程式範本。  
  
4.  儲存 SimpleProject.vstemplate 檔案。  
  
5.  在.csproj 檔案中，加入\<OutputSubPath > 每 ZipProject 項目。 卸載專案，之前，並編輯專案檔。  
  
6.  找出\<ZipProject > 項目。 每個\<ZipProject > 項目，加入\<OutputSubPath > 項目，並給定值主控台。 ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  加入這個\<PropertyGroup > 加入專案檔：  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  儲存專案檔，並重新載入專案。  
  
## <a name="testing-the-project-type-child-node"></a>測試專案類型的子節點  
 測試修改過的專案檔案，以查看是否**主控台**子節點會出現在**新專案** 對話方塊。  
  
1.  執行**重設 Microsoft Visual Studio 實驗執行個體**工具。  
  
2.  重建 SimpleProject 專案並開始偵錯。 實驗執行個體應該會出現  
  
3.  在**新專案**] 對話方塊中，按一下 [ **SimpleProject**節點。 **主控台應用程式**範本應該會出現在**範本**窗格。  
  
4.  展開**SimpleProject**節點。 **主控台**子節點應該會出現。 **SimpleProject 應用程式**範本仍會出現在**範本**窗格。  
  
5.  。 按一下**取消**和停止偵錯  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>取代的專案範本參數  
 [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)示範如何覆寫`ProjectNode.AddFileFromTemplate`方法，以進行基本的一種範本參數替代。 本節將教導您如何使用更複雜的 Visual Studio 範本參數。  
  
 當您使用中的 Visual Studio 範本建立專案時**新專案**對話方塊中，參數會被取代的範本字串，以自訂專案。 樣板參數是特殊的語彙基元開始和結束都錢幣符號，例如 $time$。 下列兩個參數是特別適用於啟用以範本為基礎的專案中的自訂項目：  
  
-   新的 Guid 取代為 [1-10] $GUID$。 您可以指定最多 10 個唯一的 Guid，例如 $guid1$。  
  
-   $safeprojectname$ 是中的使用者所提供的名稱**新專案**對話方塊中，修改以移除所有 unsafe 字元和空格。  
  
 如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。  如果您想要建立您自己的自訂範本參數，請參閱[NIB： 如何： 將自訂參數傳遞至範本](http://msdn.microsoft.com/en-us/5bc2ad11-84c7-4683-a276-e5e00d85d8fb)。  
  
#### <a name="to-substitute-project-template-parameters"></a>若要取代的專案範本參數  
  
1.  在 SimpleProjectNode.cs 檔案中，移除`AddFileFromTemplate`方法。  
  
2.  在 \Templates\Projects\ConsoleApp\SimpleProject.myproj 檔案中，找出\<RootNamespace > 屬性並將其值變更為 $safeprojectname$。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  在 \Templates\Projects\SimpleProject\Program.cs 檔案中，取代下列程式碼檔案的內容：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  重建 SimpleProject 專案並開始偵錯。 實驗執行個體應該會出現。  
  
5.  建立新的 SimpleProject 主控台應用程式。 (在**專案類型**窗格中，選取**SimpleProject**。 底下**Visual Studio 安裝的範本**，選取**主控台應用程式**。)  
  
6.  在新建的專案中，開啟 Program.cs。 看起來應該如下所示 （在檔案中的 GUID 值將會不同）。:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>建立在專案屬性頁  
 讓使用者可以檢視並變更您的範本為基礎的專案中的屬性，您可以建立您的專案類型的屬性頁。 本節說明如何建立組態無關的屬性頁。 此基本屬性頁會使用屬性方格來顯示您在您的屬性頁類別公開的公用屬性。  
  
 從您屬性頁類別的衍生`SettingsPage`基底類別。 所提供的 [屬性] 方格`SettingsPage`類別可感知的最基本資料型別，而且知道如何顯示它們。  此外，`SettingsPage`類別知道如何保存至專案檔的屬性值。  
  
 您在這一節中建立屬性頁可讓您變更和儲存這些專案屬性：  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace。  
  
1.  在 SimpleProjectPackage.cs 檔案中，加入下列`ProvideObject`屬性`SimpleProjectPackage`類別：  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))]  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     如此會註冊屬性頁類別`GeneralPropertyPage`com  
  
2.  在 SimpleProjectNode.cs 檔案中，加入至這兩個覆寫的方法`SimpleProjectNode`類別：  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
    }  
    protected override Guid[] GetPriorityProjectDesignerPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
         return result;  
    }  
    ```  
  
     這兩種方法傳回屬性頁 Guid 的陣列。  GeneralPropertyPage GUID 是唯一的項目，在陣列中，所以**屬性頁**對話方塊將會顯示一個頁面。  
  
3.  加入名為 GeneralPropertyPage.cs SimpleProject 專案的類別檔案。  
  
4.  使用下列程式碼取代此檔案的內容：  
  
    ```  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Project;  
    using System.ComponentModel;  
  
    namespace SimpleProject  
    {  
        [ComVisible(true)]  
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
        public class GeneralPropertyPage : SettingsPage  
        {  
            private string assemblyName;  
            private OutputType outputType;  
            private string defaultNamespace;  
  
            public GeneralPropertyPage()  
            {  
                this.Name = "General";  
            }  
  
            [Category("AssemblyName")]  
            [DisplayName("AssemblyName")]  
            [Description("The output file holding assembly metadata.")]  
            public string AssemblyName  
            {  
                get { return this.assemblyName; }  
            }  
            [Category("Application")]  
            [DisplayName("OutputType")]  
            [Description("The type of application to build.")]  
            public OutputType OutputType  
            {  
                get { return this.outputType; }  
                set { this.outputType = value; this.IsDirty = true; }  
            }  
            [Category("Application")]  
            [DisplayName("DefaultNamespace")]  
            [Description("Specifies the default namespace for added items.")]  
            public string DefaultNamespace  
            {  
                get { return this.defaultNamespace; }  
                set { this.defaultNamespace = value; this.IsDirty = true; }  
            }  
  
            protected override void BindProperties()  
            {  
                this.assemblyName = this.ProjectMgr.GetProjectProperty(  
    "AssemblyName", true);  
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
    "RootNamespace", false);  
  
                string outputType = this.ProjectMgr.GetProjectProperty(  
    "OutputType", false);  
                this.outputType =   
    (OutputType)Enum.Parse(typeof(OutputType), outputType);  
            }  
  
            protected override int ApplyChanges()  
            {  
                this.ProjectMgr.SetProjectProperty(  
    "AssemblyName", this.assemblyName);  
                this.ProjectMgr.SetProjectProperty(  
    "OutputType", this.outputType.ToString());  
                this.ProjectMgr.SetProjectProperty(  
    "RootNamespace", this.defaultNamespace);  
                this.IsDirty = false;  
  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    ```  
  
     `GeneralPropertyPage`類別會公開三個公用屬性 AssemblyName、 OutputType 和 RootNamespace。 AssemblyName 有沒有 set 方法，因為它會顯示為唯讀屬性。 OutputType 是列舉的常數，因此它會顯示為下拉式清單中。  
  
     `SettingsPage`基底類別提供`ProjectMgr`保存屬性。 `BindProperties`方法會使用`ProjectMgr`擷取保存的屬性值，並設定對應的屬性。  `ApplyChanges`方法會使用`ProjectMgr`取得屬性的值，並將其保存至專案檔。 設定屬性的方法會設定`IsDirty`設定為 true，表示屬性具有保存。  當您儲存專案或方案時，就會發生持續性。  
  
5.  重建 SimpleProject 方案，並開始偵錯。 實驗執行個體應該會出現。  
  
6.  在實驗執行個體，建立新的 SimpleProject 應用程式。  
  
7.  Visual Studio 會呼叫您專案的 factory 使用 Visual Studio 範本建立專案。 程式碼編輯器中開啟新的 Program.cs 檔案。  
  
8.  以滑鼠右鍵按一下專案節點中的**方案總管] 中**，然後按一下 [**屬性**。 [屬性頁] 對話方塊隨即出現。  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>測試專案屬性頁面  
 現在您可以測試是否可以修改，並變更屬性值。  
  
1.  在**MyConsoleApplication 屬性頁**對話方塊中，變更**DefaultNamespace**至**MyApplication**。  
  
2.  選取**OutputType**屬性，然後再選取**類別庫**。  
  
3.  按一下**套用**，然後按一下 **確定**。  
  
4.  重新開啟**屬性頁**對話方塊方塊中，並確認已經保存您的變更。  
  
5.  關閉 Visual Studio 的實驗執行個體。  
  
6.  重新開啟實驗執行個體。  
  
7.  重新開啟**屬性頁**對話方塊方塊中，並確認已經保存您的變更。  
  
8.  關閉 Visual Studio 的實驗執行個體。  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")