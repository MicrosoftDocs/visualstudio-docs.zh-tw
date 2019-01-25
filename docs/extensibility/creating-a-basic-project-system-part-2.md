---
title: 建立基本的專案系統，第 2 部分 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c4daab3ef0a045e1c352f170282db5e0189da3b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800044"
---
# <a name="create-a-basic-project-system-part-2"></a>建立基本專案系統，第 2 部分
在此系列中，第一個逐步解說[建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)，示範如何建立基本的專案系統。 本逐步解說建立基本專案系統上加上 Visual Studio 範本、 屬性頁和其他功能。 您必須先完成第一個逐步解說，才能啟動它。  
  
 本逐步解說將說明如何建立具有專案副檔名的專案類型 *.myproj*。 若要完成本逐步解說，您不必建立您自己的語言，因為現有的 Visual C# 專案系統會藉助本逐步解說。  
  
 本逐步解說將說明如何完成這些工作：  
  
-   建立 Visual Studio 範本。  
  
-   部署 Visual Studio 範本。  
  
-   建立中的專案類型子節點**新的專案** 對話方塊。  
  
-   啟用 Visual Studio 範本中的參數替代。  
  
-   建立在專案屬性頁。  
  
> [!NOTE]
>  在本逐步解說的步驟是以 C# 專案為基礎。 不過，除了例如副檔名的檔案和程式碼的詳細資訊，您可以使用相同的步驟針對 Visual Basic 專案。  
  
## <a name="create-a-visual-studio-template"></a>建立 Visual Studio 範本  
 [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)示範如何建立基本的專案範本，並將它新增至專案系統。 它也會示範如何使用 Visual Studio 中註冊此範本，使用<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>屬性，其會將寫入的完整路徑*\\Templates\Projects\SimpleProject\\*系統中的資料夾登錄中。  
  
 使用 Visual Studio 範本 (*.vstemplate*檔案) 而不是基本的專案範本，您可以控制的範本顯示於**新的專案** 對話方塊中，以及範本參數取代。  A *.vstemplate*檔案是 XML 檔案，描述使用專案系統範本建立專案時要包含的原始程式檔的方式。 專案系統本身是藉由收集 *.vstemplate*檔案和原始程式檔中的 *.zip*檔案，並藉由複製部署 *.zip*檔案的位置Visual studio 的已知。 更多詳細資料，在此逐步解說稍後會說明此程序。  
  
1. 在  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，開啟您依照建立 SimpleProject 方案[建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)。  
  
2. 在  *SimpleProjectPackage.cs*檔案中，尋找 ProvideProjectFactory 屬性。 取代 null，第二個參數 （專案名稱） 和第四個參數 （專案範本資料夾的路徑） 」。\\\NullPath"、，如下所示。  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. 新增名為 XML 檔案*SimpleProject.vstemplate*要*\\Templates\Projects\SimpleProject\\*資料夾。  
  
4. 內容取代*SimpleProject.vstemplate*為下列程式碼。  
  
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
  
5. 在 **屬性**視窗中，選取所有五個檔案中*\\Templates\Projects\SimpleProject\\*資料夾，然後設定**建置動作**若要**ZipProject**。  
  
   ![簡單的專案資料夾](../extensibility/media/simpproj2.png "SimpProj2")  
  
   \<TemplateData > 區段決定的位置和 SimpleProject 專案類型中的外觀**新的專案**對話方塊，如下所示：  
  
- \<名稱 > 項目名稱是 SimpleProject 應用程式的專案範本。  
  
- \<描述 > 項目包含會出現在描述**新的專案**對話方塊中，選取 [專案] 範本時。  
  
- \<圖示 > 項目會指定所顯示 SimpleProject 專案類型的圖示。  
  
- \<ProjectType > 項目名稱中的專案類型**新的專案** 對話方塊。 此名稱將專案名稱的參數取代 ProvideProjectFactory 屬性。  
  
  > [!NOTE]
  >  \<ProjectType > 項目必須符合`LanguageVsTemplate`引數`ProvideProjectFactory`SimpleProjectPackage.cs 檔案中的屬性。  
  
  \<TemplateContent > 一節將說明這些新的專案建立時產生的檔案：  
  
- *SimpleProject.myproj*  
  
- *Program.cs*  
  
- *AssemblyInfo.cs*  
  
  這三個檔案有`ReplaceParameters`設為 true，可讓參數替代。  *Program.cs*檔案具有`OpenInEditor`設為 true，這會導致要建立專案時，程式碼編輯器中開啟的檔案。  
  
  如需 Visual Studio 範本結構描述中元素的詳細資訊，請參閱[Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
> [!NOTE]
>  如果專案具有一個以上的 Visual Studio 範本，每個範本是在不同的資料夾。 在該資料夾中的每個檔案必須有**建置動作**設為**ZipProject**。  
  
## <a name="adding-a-minimal-vsct-file"></a>將最小.vsct 檔案  
 Visual Studio 必須以辨識新的或修改 Visual Studio 範本的安裝模式執行。 安裝模式需要 *.vsct*檔案會出現。 因此，您必須新增最低限度 *.vsct*檔案加入專案。  
  
1.  新增名為 XML 檔案*SimpleProject.vsct* SimpleProject 專案。  
  
2.  內容取代*SimpleProject.vsct*為下列程式碼的檔案。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  設定**建置動作**的這個檔案來**VSCTCompile**。 您可以這樣做只在 *.csproj*檔案，無法顯示於**屬性**視窗。 請確定**建置動作**這個檔案設定為**無**此時。  
  
    1.  以滑鼠右鍵按一下 [SimpleProject] 節點，然後按一下**編輯 SimpleProject.csproj**。  
  
    2.  在  *.csproj*檔案，找出*SimpleProject.vsct*項目。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  變更 建置動作設為**VSCTCompile**。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  專案檔案並關閉編輯器。  
  
    5.  儲存 SimpleProject] 節點，然後在**方案總管**按一下 [**重新載入專案**。  
  
## <a name="examine-the-visual-studio-template-build-steps"></a>檢查 Visual Studio 範本建置步驟  
 通常在安裝模式下執行 Visual Studio 的 VSPackage 專案建置系統時 *.vstemplate*檔案變更時，或其中所包含專案 *.vstemplate*檔就會重建。 您可以照著藉由設定 MSBuild 的詳細資訊層級設為 Normal 或更高版本。  
  
1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2. 依序展開**專案和方案**節點，，然後選取**建置並執行**。  
  
3. 設定**MSBuild 專案建置輸出詳細等級**要**Normal**。 按一下 [確定 **Deploying Office Solutions**]。  
  
4. 重建 SimpleProject 專案。  
  
   若要建立的組建步驟 *.zip*專案檔看起來應該像下列的範例。  
  
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
  
## <a name="deploy-a-visual-studio-template"></a>部署 Visual Studio 範本  
 Visual Studio 範本不包含路徑資訊。 因此，範本 *.zip*檔案必須部署至 Visual Studio 已知的位置。 ProjectTemplates 資料夾的位置通常是 *< %LOCALAPPDATA%> \Microsoft\VisualStudio\14.0Exp\ProjectTemplates*。  
  
 若要部署您的專案 factory，安裝程式必須具有系統管理員權限。 它會部署在 Visual Studio 的 [安裝] 節點下的範本： *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*。  
  
## <a name="test-a-visual-studio-template"></a>測試 Visual Studio 範本  
 測試您的專案處理站，以查看是否使用 Visual Studio 範本建立專案階層架構。  
  
1. 重設 Visual Studio SDK experimental 執行個體。  
  
    在 [!INCLUDE[win7](../debugger/includes/win7_md.md)]:在 [**開始**] 功能表中，尋找**Microsoft Visual Studio/Microsoft Visual Studio SDK/工具**資料夾，然後再選取**重設 Microsoft Visual Studio 實驗執行個體**.  
  
    在較新版 Windows 的詳細資訊：在 **開始**畫面上，輸入**重設 Microsoft Visual Studio\<版本 > 實驗性執行個體**。  
  
2. 命令提示字元 視窗隨即出現。 您會看到字樣**按下任意鍵繼續**，按一下**ENTER**。 在視窗關閉後，開啟 Visual Studio。  
  
3. 重建 SimpleProject 專案並開始偵錯。 實驗執行個體隨即出現。  
  
4. 在實驗執行個體中，建立 SimpleProject 專案。 在 **新的專案**對話方塊中，選取**SimpleProject**。  
  
5. 您應該會看到 SimpleProject 的新執行個體。  
  
   ![簡單專案的新執行個體](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
   ![我專案的新執行個體](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="create-a-project-type-child-node"></a>建立專案類型的子節點  
 您可以將子節點新增至中的專案類型節點**新的專案** 對話方塊。  比方說，SimpleProject 專案類型中，您可能有子節點的主控台應用程式視窗的應用程式、 web 應用程式等等。  
  
 子節點藉由變更專案檔，並新增\<OutputSubPath > 子系\<ZipProject > 項目。 複製範本時，建置或部署期間，每個子節點會成為專案範本資料夾的子資料夾。  
  
 本節說明如何建立主控台 SimpleProject 專案類型的子節點。  
  
1.  重新命名*\\Templates\Projects\SimpleProject\\*資料夾 *\\Templates\Projects\ConsoleApp\\*。  
  
2.  在 **屬性**視窗中，選取所有五個中的檔案*\\Templates\Projects\ConsoleApp\\*資料夾，並確定**建置動作**設為**ZipProject**。  
  
3.  在 SimpleProject.vstemplate 檔案中加入下面這一行的結尾\<TemplateData > 區段中的，將結尾標記之前。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     這會導致出現在 [主控台] 子節點和 SimpleProject 父節點，也就是子節點上的一層中的主控台應用程式範本。  
  
4.  儲存*SimpleProject.vstemplate*檔案。  
  
5.  在  *.csproj*檔案中，新增\<OutputSubPath > 每個 ZipProject 項目。 卸載專案，與之前，並編輯專案檔。  
  
6.  找出\<ZipProject > 項目。 每個\<ZipProject > 項目，新增\<OutputSubPath > 項目並為它提供主控台的值。 ZipProject  
  
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
  
7.  將此新增\<PropertyGroup > 專案檔：  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  儲存專案檔，並重新載入專案。  
  
## <a name="test-the-project-type-child-node"></a>測試專案類型的子節點  
 測試修改過的專案檔案，以查看是否**主控台**子節點會出現在**新的專案** 對話方塊。  
  
1. 執行**重設 Microsoft Visual Studio 實驗執行個體**工具。  
  
2. 重建 SimpleProject 專案並開始偵錯。 實驗執行個體應該會出現  
  
3. 在 [**新的專案**] 對話方塊中，按一下**SimpleProject**節點。 **主控台應用程式**範本應該會出現在**範本**窗格。  
  
4. 依序展開**SimpleProject**節點。 **主控台**子節點應該會出現。 **SimpleProject 應用程式**範本仍會出現在**範本**窗格。  
  
5. 按一下 **取消**並停止偵錯。  
  
   ![簡單專案彙總](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
   ![簡單專案主控台節點](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substitute-project-template-parameters"></a>替代的專案範本參數  
 [建立基本的專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)示範如何覆寫`ProjectNode.AddFileFromTemplate`方法來執行基本的一種範本參數替代。 本章節將說明如何使用更複雜的 Visual Studio 範本參數。  
  
 當您使用 Visual Studio 範本中的，會在建立專案時**新的專案** 對話方塊中，若要自訂專案範本會以取代參數字串。 樣板參數是一種特殊的權杖，開頭和結尾貨幣符號，例如 $time$。 下列兩個參數是啟用自訂範本為基礎的專案中特別有用：  
  
- 新的 Guid 取代 $GUID [1-10] $。 您可以指定最多 10 個唯一的 Guid，例如 $guid1$。  
  
- $safeprojectname$ 是中的使用者所提供的名稱**新的專案**對話方塊中，修改以移除所有 unsafe 字元和空格。  
  
  如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。  
  
### <a name="to-substitute-project-template-parameters"></a>若要替代專案範本的參數  
  
1.  在  *SimpleProjectNode.cs*檔案中，移除`AddFileFromTemplate`方法。  
  
2.  在   *\\Templates\Projects\ConsoleApp\SimpleProject.myproj*檔案中，找出\<RootNamespace > 屬性並將其值變更為 $safeprojectname$。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  在   *\\Templates\Projects\SimpleProject\Program.cs*檔案中，以下列程式碼取代檔案的內容：  
  
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
  
6.  在新建的專案中，開啟*Program.cs*。 看起來應該如下所示 （在檔案中的 GUID 值會不同）。:  
  
    ```csharp  
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
  
## <a name="create-a-project-property-page"></a>建立在專案屬性頁  
 讓使用者可以檢視和變更您的範本為基礎的專案中的屬性時，您便可以建立您的專案類型的屬性頁。 本節將說明如何建立獨立設定的屬性頁。 這個基本的屬性頁會使用 [屬性] 方格來顯示屬性頁類別中公開 （expose） 的公用屬性。  
  
 衍生您的屬性頁面類別，從`SettingsPage`基底類別。 所提供的 [屬性] 方格`SettingsPage`類別是留意最基本的資料型別，而且知道如何顯示它們。  颾魤 ㄛ`SettingsPage`類別知道如何保存至專案檔的屬性值。  
  
 您在這一節中建立屬性頁可讓您變更並儲存這些專案屬性：  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace。  
  
1. 在  *SimpleProjectPackage.cs*檔案中，新增這`ProvideObject`屬性設定為`SimpleProjectPackage`類別：  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    這會註冊屬性頁類別`GeneralPropertyPage`com。  
  
2. 在  *SimpleProjectNode.cs*檔案中，新增至這兩個覆寫的方法`SimpleProjectNode`類別：  
  
   ```csharp  
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
  
    這兩種方法會傳回屬性頁 Guid 的陣列。  GeneralPropertyPage GUID 是唯一的項目，在陣列中，因此**屬性頁**對話方塊將會顯示只有一頁。  
  
3. 將類別檔案命名為*GeneralPropertyPage.cs* SimpleProject 專案。  
  
4. 使用下列程式碼取代此檔案的內容：  
  
   ```csharp  
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
  
    `GeneralPropertyPage`類別會公開三個公用屬性組件名稱、 OutputType 和 RootNamespace。 因為組件名稱不具 set 方法，它會顯示為唯讀屬性。 OutputType 是列舉的常數，因此它會顯示為下拉式清單中。  
  
    `SettingsPage`基底類別提供`ProjectMgr`保存的屬性。 `BindProperties`方法會使用`ProjectMgr`擷取保存的屬性值，並設定對應的屬性。  `ApplyChanges`方法會使用`ProjectMgr`取得屬性的值，並將其保存至專案檔。 設定屬性的方法會設定`IsDirty`表示的屬性具有保存為 true。  當您儲存的專案或方案時，就會發生持續性。  
  
5. 重建 SimpleProject 方案並開始偵錯。 實驗執行個體應該會出現。  
  
6. 在實驗執行個體中，建立新的 SimpleProject 應用程式。  
  
7. Visual Studio 會呼叫您專案的處理站使用 Visual Studio 範本建立專案。 新*Program.cs*程式碼編輯器中開啟檔案。  
  
8. 以滑鼠右鍵按一下專案節點，在**方案總管**，然後按一下**屬性**。 [屬性頁] 對話方塊隨即出現。  
  
   ![簡單的專案屬性頁](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="test-the-project-property-page"></a>測試專案屬性頁面
 現在您可以測試是否可以修改，並變更屬性值。  
  
1. 在 [ **MyConsoleApplication 屬性頁**] 對話方塊中，變更**DefaultNamespace**來**MyApplication**。  
  
2. 選取  **OutputType**屬性，，然後選取**類別庫**。  
  
3. 按一下 **套用**，然後按一下**確定**。  
  
4. 重新開啟**屬性頁**對話方塊方塊中，並確認您的變更已保存。  
  
5. 關閉 Visual Studio 的實驗執行個體。  
  
6. 重新開啟實驗的執行個體。  
  
7. 重新開啟**屬性頁**對話方塊方塊中，並確認您的變更已保存。  
  
8. 關閉 Visual Studio 的實驗執行個體。  
  
   ![關閉實驗執行個體](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
