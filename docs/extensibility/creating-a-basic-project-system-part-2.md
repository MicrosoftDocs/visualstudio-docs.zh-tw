---
title: 建立基本的專案系統，第2部分 |Microsoft Docs
description: 瞭解如何將 Visual Studio 範本、屬性頁和其他功能新增至先前文章中建立的專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ceef95f90d2f54ad7b527ccc8c00322c77491fb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853148"
---
# <a name="create-a-basic-project-system-part-2"></a>建立基本的專案系統，第2部分
本系列的第一個逐步解說會 [建立基本的專案系統，第1部分](../extensibility/creating-a-basic-project-system-part-1.md)顯示如何建立基本的專案系統。 本逐步解說會透過新增 Visual Studio 範本、屬性頁及其他功能，以基本專案系統為基礎。 您必須先完成第一個逐步解說，然後再開始這一項。

本逐步解說會教您如何建立專案副檔名為 *myproj.csproj* 的專案類型。 若要完成本逐步解說，您不需要建立自己的語言，因為逐步解說會從現有的 Visual c # 專案系統中借用。

本逐步解說會教您如何完成這些工作：

- 建立 Visual Studio 範本。

- 部署 Visual Studio 範本。

- 在 [ **新增專案** ] 對話方塊中，建立專案類型的子節點。

- 啟用 Visual Studio 範本中的參數替代。

- 建立專案屬性頁。

> [!NOTE]
> 本逐步解說中的步驟是以 c # 專案為基礎。 但是，除了副檔名和程式碼以外，您也可以針對 Visual Basic 專案使用相同的步驟。

## <a name="create-a-visual-studio-template"></a>建立 Visual Studio 範本
- [建立基本的專案系統，第1部分](../extensibility/creating-a-basic-project-system-part-1.md) 顯示如何建立基本專案範本，並將它加入至專案系統。 它也會示範如何使用屬性將此範本註冊 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> ，這會在系統登錄中寫入 *\\ Templates\Projects\SimpleProject \\* 資料夾的完整路徑。

藉由使用 Visual Studio 範本 (*.vstemplate* 檔) 而不是基本專案範本，您可以控制範本在 [ **新增專案** ] 對話方塊中的顯示方式，以及如何替代範本參數。 *.Vstemplate* 檔案是一種 XML 檔案，描述當使用專案系統範本建立專案時，如何包含原始程式檔。 專案系統本身的建立方式，是在 *.zip* 檔案中收集 *.vstemplate* 檔案和原始程式檔，然後藉由將 .zip 檔案複製到已知要 Visual Studio 的位置來部署 *。* 本逐步解說稍後會更詳細地說明此程式。

1. 在中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，開啟您透過下列 [建立基本專案系統（第1部分）](../extensibility/creating-a-basic-project-system-part-1.md)所建立的 SimpleProject 方案。

2. 在 *SimpleProjectPackage.cs* 檔案中，尋找 ProvideProjectFactory 屬性。 以 null 取代 (專案名稱) 的第二個參數，而第四個參數 (專案範本資料夾的路徑，) 為 "。 \\\NullPath "，如下所示。

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. 將名為 *SimpleProject* 的 XML 檔案加入至 *\\ Templates\Projects\SimpleProject \\* 資料夾。

4. 以下列程式碼取代 *SimpleProject* 的內容。

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

5. 在 [**屬性**] 視窗中，選取 [ *\\ Templates\Projects\SimpleProject \\* ] 資料夾中的五個檔案，然後將 [**組建] 動作** 設定為 [ **ZipProject**]。

    ![簡易專案資料夾](../extensibility/media/simpproj2.png "SimpProj2")

    \<TemplateData>區段會在 [**新增專案**] 對話方塊中決定 SimpleProject 專案類型的位置和外觀，如下所示：

- \<Name>元素會將專案範本命名為 SimpleProject 應用程式。

- \<Description>專案包含選取專案範本時，出現在 [**新增專案**] 對話方塊中的描述。

- \<Icon>元素指定與 SimpleProject 專案類型一起出現的圖示。

- \<ProjectType>元素會在 [**新增專案**] 對話方塊中命名專案類型。 這個名稱會取代 ProvideProjectFactory 屬性的專案名稱參數。

  > [!NOTE]
  > \<ProjectType>元素必須符合 SimpleProjectPackage.cs 檔 `LanguageVsTemplate` 中屬性的引數 `ProvideProjectFactory` 。

  \<TemplateContent>本節說明在建立新專案時所產生的這些檔案：

- *SimpleProject. myproj.csproj*

- *Program.cs*

- *AssemblyInfo.cs*

  這三個檔案都已 `ReplaceParameters` 設為 true，以啟用參數替代。 *Program.cs* 檔案已 `OpenInEditor` 設定為 true，這會在建立專案時，在程式碼編輯器中開啟檔案。

  如需 Visual Studio 範本架構中專案的詳細資訊，請參閱 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)。

> [!NOTE]
> 如果專案有一個以上的 Visual Studio 範本，每個範本都位於不同的資料夾中。 該資料夾中的每個檔案都必須將 **組建動作** 設為 **ZipProject**。

## <a name="adding-a-minimal-vsct-file"></a>新增 .vsct 檔案
 Visual Studio 必須在安裝模式中執行，才能辨識新的或修改過的 Visual Studio 範本。 安裝模式需要有 *.vsct* 檔。 因此，您必須將 *.vsct* 檔案新增至專案。

1. 將名為 *SimpleProject* 的 XML 檔案加入至 SimpleProject 專案。

2. 以下列程式碼取代 *SimpleProject. .vsct* 檔案的內容。

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. 將此檔案的 [ **組建] 動作** 設定為 [ **VSCTCompile**]。 您只能在 *.csproj* 檔案中，而不是在 [ **屬性** ] 視窗中進行這項作業。 請確定此檔案的 [ **建立] 動作** 在此時設定為 [ **無** ]。

    1. 在 [SimpleProject] 節點上按一下滑鼠右鍵，然後按一下 [ **編輯 SimpleProject**]。

    2. 在 *.csproj* 檔案中，找出 *SimpleProject .vsct* 專案。

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. 將 [組建] 動作變更為 **VSCTCompile**。

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. 專案檔，然後關閉編輯器。

    5. 儲存 [SimpleProject] 節點，然後在 **方案總管** 按一下 [ **重載專案**]。

## <a name="examine-the-visual-studio-template-build-steps"></a>檢查 Visual Studio 範本的組建步驟
 當 *.vstemplate* 檔案變更或重建包含 *.vstemplate* 檔案的專案時，VSPackage 專案組建系統通常會在安裝程式模式中執行 Visual Studio。 您可以將 MSBuild 的詳細資訊層級設定為 Normal 或更高的版本。

1. 在 **[工具]** 功能表上，按一下 **[選項]** 。

2. 展開 [ **專案和方案** ] 節點，然後選取 [ **建立並執行**]。

3. 將 **MSBuild 專案組建輸出詳細** 資訊設定為 [ **一般**]。 按一下 [確定]  。

4. 重建 SimpleProject 專案。

    建立 *.zip* 專案檔的組建步驟應該類似于下列範例。

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
Visual Studio 範本不包含路徑資訊。 因此，必須將範本 *.zip* 檔案部署至已知 Visual Studio 的位置。 >\templates\projecttemplates\csharp\helloworld\ 資料夾的位置通常是 *<% LOCALAPPDATA% > \microsoft\visualstudio\14.0exp\projecttemplates*。

若要部署您的 project factory，安裝程式必須具有系統管理員許可權。 它會在 Visual Studio 安裝節點下部署範本： *. ..\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates*。

## <a name="test-a-visual-studio-template"></a>測試 Visual Studio 範本
測試您的 project factory，以查看它是否使用 Visual Studio 範本建立專案階層。

1. 重設 Visual Studio SDK 實驗實例。

    在 [!INCLUDE[win7](../debugger/includes/win7_md.md)] ：在 [ **開始** ] 功能表上，尋找 [ **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** ] 資料夾，然後選取 **[重設 Microsoft Visual Studio 實驗實例**]。

    在更新版本的 Windows 上：在 [ **開始** ] 畫面上，輸入 **[重設 Microsoft Visual Studio \<version> 實驗實例**]。

2. [命令提示字元] 視窗隨即出現。 當您看到單字 **按任意鍵繼續** 時，請按一下 **enter**。 視窗關閉之後，開啟 Visual Studio。

3. 重建 SimpleProject 專案並開始進行調試。 實驗實例隨即出現。

4. 在實驗實例中，建立 SimpleProject 專案。 在 [ **新增專案** ] 對話方塊中，選取 [ **SimpleProject**]。

5. 您應該會看到 SimpleProject 的新實例。

    ![簡單專案的新實例](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![我的專案新實例](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>建立專案類型的子節點
您可以在 [ **新增專案** ] 對話方塊中，將子節點加入至 [專案類型] 節點。 例如，針對 SimpleProject 專案類型，您可能會有適用于主控台應用程式、視窗應用程式、web 應用程式等的子節點。

藉由改變專案檔並將子系加入至專案，即可建立子節點 \<OutputSubPath> \<ZipProject> 。 在組建或部署期間複製範本時，每個子節點都會變成 [專案範本] 資料夾的子資料夾。

本節說明如何建立 SimpleProject 專案類型的主控台子節點。

1. 將 *\\ Templates\Projects\SimpleProject \\* 資料夾重新命名為 *\\ Templates\Projects\ConsoleApp \\*。

2. 在 [**屬性**] 視窗中，選取 [ *\\ Templates\Projects\ConsoleApp \\* ] 資料夾中的五個檔案，並確定 [**組建] 動作** 設定為 [ **ZipProject**]。

3. 在 SimpleProject .vstemplate 檔案中，于區段的結尾處加入下列 \<TemplateData> 這一行，緊接在結束記號之前。

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    這會導致主控台應用程式範本同時出現在主控台子節點和 SimpleProject 父節點中，這是子節點上方的一層。

4. 儲存 *SimpleProject .vstemplate* 檔案。

5. 在 *.csproj* 檔案中，加入 \<OutputSubPath> 每個 ZipProject 元素。 如同之前一樣卸載專案，然後編輯專案檔。

6. 尋找 \<ZipProject> 元素。 在每個專案 \<ZipProject> 中加入專案， \<OutputSubPath> 並為它提供值主控台。 ZipProject

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

7. 將此 \<PropertyGroup> 專案新增至專案檔：

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. 儲存專案檔案，然後重載專案。

## <a name="test-the-project-type-child-node"></a>測試專案類型的子節點
測試已修改的專案檔，以查看 **主控台** 子節點是否出現在 [ **新增專案** ] 對話方塊中。

1. 執行 [ **重設 Microsoft Visual Studio 實驗實例** ] 工具。

2. 重建 SimpleProject 專案並開始進行調試。 實驗實例應會出現

3. 在 [ **新增專案** ] 對話方塊中，按一下 [ **SimpleProject** ] 節點。 **主控台應用程式** 範本應該會出現在 [**範本**] 窗格中。

4. 展開 [ **SimpleProject** ] 節點。 **主控台** 子節點應會出現。 **SimpleProject 應用程式** 範本會繼續出現在 [**範本**] 窗格中。

5. 按一下 [ **取消** ] 和 [停止調試]。

    ![簡易專案匯總](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![簡易專案主控台節點](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>替代專案範本參數
- [建立基本的專案系統，第1部分](../extensibility/creating-a-basic-project-system-part-1.md) 示範如何覆寫 `ProjectNode.AddFileFromTemplate` 方法，以進行基本的樣板參數替代。 本節說明如何使用更精密的 Visual Studio 範本參數。

當您使用 [ **新增專案** ] 對話方塊中的 Visual Studio 範本建立專案時，會以自訂專案的字串取代範本參數。 範本參數是以貨幣符號開頭和結尾的特殊權杖，例如 $time $。 下列兩個參數特別適用于在以範本為基礎的專案中啟用自訂：

- $GUID [1-10] $ 取代為新的 Guid。 您最多可以指定10個唯一的 Guid，例如 $guid $1。

- $safeprojectname $ 是使用者在 [ **新增專案** ] 對話方塊中提供的名稱，修改為移除所有不安全的字元和空格。

  如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。

### <a name="to-substitute-project-template-parameters"></a>替代專案範本參數

1. 在 *SimpleProjectNode.cs* 檔案中，移除 `AddFileFromTemplate` 方法。

2. 在 *\\ Templates\Projects\ConsoleApp\SimpleProject.myproj* 檔案中，找出 \<RootNamespace> 屬性，並將其值變更為 $safeprojectname $。

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. 在 *\\ Templates\Projects\SimpleProject\Program.cs* 檔案中，以下列程式碼取代檔案的內容：

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

4. 重建 SimpleProject 專案並開始進行調試。 實驗實例應會出現。

5. 建立新的 SimpleProject 主控台應用程式。  (在 [ **專案類型** ] 窗格中，選取 [ **SimpleProject**]。 在 [ **Visual Studio 安裝的範本**] 下，選取 [ **主控台應用程式**]。 ) 

6. 在新建立的專案中，開啟 *Program.cs*。 您的檔案看起來應該會像下面這樣 (GUID 值將有所不同。 ) ：

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

## <a name="create-a-project-property-page"></a>建立專案屬性頁
您可以建立專案類型的屬性頁，讓使用者可以根據您的範本，來查看和變更專案中的屬性。 本節說明如何建立與設定無關的屬性頁面。 這個基本屬性頁面會使用屬性方格來顯示您在屬性頁類別中公開的公用屬性。

從基類衍生您的屬性頁類別 `SettingsPage` 。 類別所提供的屬性方格 `SettingsPage` 可感知最基本的資料類型，並知道如何顯示它們。 此外，此 `SettingsPage` 類別也知道如何將屬性值保存到專案檔。

您在此區段中建立的屬性頁面可讓您變更和儲存這些專案屬性：

- AssemblyName

- OutputType

- RootNamespace.

1. 在 *SimpleProjectPackage.cs* 檔案中，將下列 `ProvideObject` 屬性新增至 `SimpleProjectPackage` 類別：

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    這會向 COM 註冊屬性頁面類別 `GeneralPropertyPage` 。

2. 在 *SimpleProjectNode.cs* 檔案中，將這兩個覆寫的方法新增至 `SimpleProjectNode` 類別：

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

    這兩種方法都會傳回屬性頁 Guid 的陣列。 GeneralPropertyPage GUID 是陣列中唯一的元素，因此 [ **屬性頁** ] 對話方塊只會顯示一個頁面。

3. 將名為 *GeneralPropertyPage.cs* 的類別檔案新增至 SimpleProject 專案。

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
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    `GeneralPropertyPage`類別會公開三個公用屬性 AssemblyName、OutputType 和 RootNamespace。 因為 AssemblyName 沒有 set 方法，所以會顯示為唯讀屬性。 OutputType 是列舉的常數，因此它會顯示為下拉式清單。

    `SettingsPage`基類會提供 `ProjectMgr` 以保存屬性。 `BindProperties`方法會使用 `ProjectMgr` 來取出保存的屬性值，並設定對應的屬性。 `ApplyChanges`方法會使用 `ProjectMgr` 來取得屬性的值，並將其保存在專案檔中。 屬性集方法會將設定 `IsDirty` 為 true，以指出必須保存屬性。 當您儲存專案或方案時，會發生持續性。

5. 重建 SimpleProject 方案並開始進行調試。 實驗實例應會出現。

6. 在實驗實例中，建立新的 SimpleProject 應用程式。

7. Visual Studio 會呼叫您的 project factory，以使用 Visual Studio 範本建立專案。 新的 *Program.cs* 檔案會在程式碼編輯器中開啟。

8. 在 **方案總管** 的專案節點上按一下滑鼠右鍵，然後按一下 [ **屬性**]。 [屬性頁面] 對話方塊隨即出現。

    ![簡單專案屬性頁](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>測試專案屬性頁
現在您可以測試是否可以修改及變更屬性值。

1. 在 [ **MyConsoleApplication 屬性頁** ] 對話方塊中，將 **DefaultNamespace** 變更為 **MyApplication**。

2. 選取 [ **OutputType** ] 屬性，然後選取 [ **類別庫**]。

3. 按一下 [套用]，然後按一下 [確定]。

4. 重新開啟 [ **屬性頁** ] 對話方塊，並確認已保存您的變更。

5. 關閉 Visual Studio 的實驗執行個體。

6. 重新開啟實驗實例。

7. 重新開啟 [ **屬性頁** ] 對話方塊，並確認已保存您的變更。

8. 關閉 Visual Studio 的實驗執行個體。
    ![關閉實驗實例](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
