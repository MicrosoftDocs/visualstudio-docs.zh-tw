---
title: 創建基本項目系統,第 2 部分 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739718"
---
# <a name="create-a-basic-project-system-part-2"></a>建立基本項目系統,第 2 部分
本系列的第一個演練"[創建基本專案系統"第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)演示如何創建基本項目系統。 本演練通過添加 Visual Studio 範本、屬性頁和其他功能建構基本項目系統。 在開始第一次演練之前,您必須完成第一次演練。

本演練將介紹如何創建具有專案檔名副檔名 *.myproj*的項目類型。 要完成演練,您不必創建自己的語言,因為演練借用了現有的 Visual C++ 專案系統。

本演練將介紹如何完成這些任務:

- 創建可視化工作室範本。

- 部署可視化工作室範本。

- 在 **「新項目」** 對話框中建立項目類型子節點。

- 在可視化工作室範本中啟用參數替換。

- 創建項目屬性頁。

> [!NOTE]
> 本演練中的步驟基於 C# 專案。 但是,除了檔名擴展名和代碼等細節外,您可以對 Visual Basic 專案使用相同的步驟。

## <a name="create-a-visual-studio-template"></a>建立視覺化工作室範本
- [創建基本項目系統,第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)演示如何創建基本專案範本並將其添加到專案系統。 它還演示如何使用<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>屬性向 Visual Studio 註冊此範本,該屬性在系統註冊表中寫入*\\範本_Project_SimpleProject\\*資料夾的完整路徑。

通過使用 Visual Studio 樣本 *(.vstemplate*檔) 而不是基本項目範本,可以控制樣本在 **「新專案」** 對話方塊中的顯示方式以及如何取代範本參數。 *.vstemplate*檔案是一個 XML 檔,用於描述如何使用專案系統範本創建專案時如何包括源檔。 專案系統本身是通過收集 *.vstemplate*檔案和 *.zip*檔案中的源檔而構建的,並通過將 *.zip*檔案複製到 Visual Studio 已知的位置進行部署。 此過程在本演練的後面部分進行了詳細介紹。

1. 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中,打開通過以下[創建基本項目系統(第1部分](../extensibility/creating-a-basic-project-system-part-1.md))創建的SimpleProject解決方案。

2. 在*SimpleProjectPackage.cs*檔中,查找"提供專案工廠"屬性。 將第二個參數(專案名稱)替換為 null,將第四個參數(專案範本資料夾的路徑)替換為"\\*NullPath",如下所示。

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. 將名為*SimpleProject.vstemplate*的 XML 檔添加到*\\\\範本\專案_ 簡單項目*資料夾。

4. 將*SimpleProject.vstemplate*的內容替換為以下代碼。

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

5. 在 **「屬性」** 視窗中, 選擇*\\\\樣本的字目_簡單專案*資料夾中的所有五個檔案,並將**產生操作**設定為**ZipProject**。

    ![簡單項目資料夾](../extensibility/media/simpproj2.png "辛普普傑2")

    「\<樣本資料>」部分確定 **「新項目」** 對話框中「簡單項目項目類型」的位置和外觀,如下所示:

- 名稱\<>元素将项目模板命名为「簡單項目應用程式」。

- "\<描述>元素包含選擇項目樣本時顯示在 **「新專案」** 對話框中的說明。

- 圖示\<>元素指定与简单项目项目类型一起显示的图标。

- 「\<項目類型> 元素在 **」新專案「** 對話框中命名項目類型」。 此名稱將替換"提供專案工廠"屬性的專案名稱參數。

  > [!NOTE]
  > ProjectType \<> 元素`LanguageVsTemplate`必須與 SimpleProjectPackage.cs 檔中`ProvideProjectFactory`的屬性參數匹配。

  樣本\<內容>部分介紹建立新項目時產生的這些檔:

- *簡單專案.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  所有三個檔`ReplaceParameters`都設置為 true,從而啟用參數替換。 *Program.cs*檔案`OpenInEditor`已 設定為 true,這將導致在創建專案時在代碼編輯器中打開該檔。

  有關可視化工作室範本架構中的元素的詳細資訊,請參閱[可視化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)。

> [!NOTE]
> 如果專案有多個 Visual Studio 範本,則每個範本都在單獨的資料夾中。 這個資料夾中的每個檔案都必須將**產生操作**設定為**ZipProject**。

## <a name="adding-a-minimal-vsct-file"></a>新增最小的 .vsct 檔案
 可視化工作室必須在設置模式下運行,以識別新的或修改的可視化工作室範本。 設定模式需要存在 *.vsct*檔。 因此,您必須向專案添加最小的 *.vsct*檔。

1. 將名為*SimpleProject.vsct 的*XML 檔添加到簡單專案專案中。

2. 將*SimpleProject.vsct*檔的內容替換為以下代碼。

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. 將此檔案產生**操作**設定為**VSCT 編譯**。 只能在 *.csproj*檔中執行此操作,不能在 **「屬性」** 視窗中執行此操作。 確保此時此檔的**生成操作**設置為 **「無**」。

    1. 右鍵單擊簡單專案節點,然後單擊 **「編輯簡單專案.csproj**」。。

    2. 在 *.csproj*檔中,找到*SimpleProject.vsct*項。

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. 將產生操作變更為**VSCT 編譯**。

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. 專案檔並關閉編輯器。

    5. 保存簡單專案節點,然後在**解決方案資源管理器**中按一下 **「重新載入專案**」。

## <a name="examine-the-visual-studio-template-build-steps"></a>檢查視覺化工作室範本產生步驟
 VSPackage 專案生成系統通常在設定模式下運行 Visual Studio,當 *.vstemplate*檔發生更改或包含 *.vstemplate*檔的專案被重建時。 通過設置 MSBuild 的詳細程度級別或更高版本,可以遵循這一點。

1. 在 **[工具]** 功能表上，按一下 **[選項]**。

2. 展開**專案和解決方案**節點,然後選擇 **"生成"和"運行**"。

3. 將**MSBuild 專案產生輸出詳細性**設置為 **「正常**」。 按一下 [確定]  。

4. 重建簡單項目專案。

    創建 *.zip*專案檔的生成步驟應類似於以下範例。

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

## <a name="deploy-a-visual-studio-template"></a>部署視覺化工作室範本
可視化工作室範本不包含路徑資訊。 因此,範本 *.zip*檔必須部署到 Visual Studio 已知的位置。 ProjectTemplates 資料夾的位置通常 *<%LOCALAPPDATA%>\微軟_VisualStudio_14.0Exp_ProjectTemplates。*

要部署專案工廠,安裝程式必須具有管理員許可權。 它在視覺化工作室安裝節點下部署樣本: *.\微軟可視化工作室 14.0\Common7_IDE_ProjectTemplates*。

## <a name="test-a-visual-studio-template"></a>測試視覺化工作室範本
測試專案工廠以查看它是否使用 Visual Studio 範本創建專案層次結構。

1. 重置可視化工作室 SDK 實驗實例。

    在[!INCLUDE[win7](../debugger/includes/win7_md.md)]:在 **「開始」** 選單上,尋找**微軟視覺工作室/微軟視覺工作室 SDK/Tools**資料夾,然後選擇 **「重置 Microsoft 視覺工作室實驗實例**」。。

    在更高版本的 Windows 上:在 **「開始」** 螢幕上,鍵入**\<「重置 Microsoft 視覺化工作室」版本>實驗實例**。

2. 將顯示命令提示視窗。 當您看到單字 **「按任意鍵繼續」 時**,按**下 ENTER**。 視窗關閉后,打開視覺工作室。

3. 重建簡單專案並開始調試。 出現實驗實例。

4. 在實驗實例中,創建一個簡單的項目專案。 在 **"新項目'** 對話方塊中,選擇 **「簡單專案**」。

5. 您應該會看到一個新實例的簡單專案。

    ![簡單專案新實體](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![我的項目新實體](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>建立項目型態子節點
您可以在 **「新項目」** 對話方塊中將子節點添加到項目類型節點。 例如,對於 SimpleProject 專案類型,可以具有主控台應用程式、視窗應用程式、Web 應用程式等的子節點。

子節點是通過更改專案檔和將輸出子路徑>\<子節點添加\<到 ZipProject>元素来创建的。 在生成或部署期間複製範本時,每個子節點將成為專案範本資料夾的子資料夾。

本節演示如何為簡單項目項目類型創建控制檯子節點。

1. 將*\\樣本\專案\簡單項目\\*資料夾重新命名為*\\樣本\專案\主控台\\應用程式*。

2. 在 **「屬性」** 視窗中,選擇*\\\\樣本\專案\主控台應用*資料夾中的所有五個檔案,並確保**產生操作**設定為**ZipProject**。

3. 在 SimpleProject.vstemplate 檔中,在結束標\<記之前的 樣本數據>部分的末尾添加以下行。

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    這將導致主控台應用程式樣本同時出現在主控台子節點和SimpleProject父節點中,該節點位於子節點上方一個級別。

4. 保存*簡單專案.vstemplate*檔案。

5. 在 *.csproj*檔\<中, 將輸出子路徑>添加到每個 ZipProject 元素。 與以前一樣卸載專案並編輯專案檔。

6. 找到\<ZipProject>元素。 到每個\<ZipProject\<>元素, 添加一個輸出子路徑>元素,並給它值主控台。 郵編專案

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

7. 將此屬性\<群組>新增到項目檔中:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. 保存專案檔並重新載入專案。

## <a name="test-the-project-type-child-node"></a>測試項目類型子節點
測試修改後的項目檔,以檢視**控制檯**子節點是否顯示在 **「新專案**」對話方塊中。

1. 運行**重置 Microsoft 視覺工作室實驗實例**工具。

2. 重建簡單專案並開始調試。 應出現實驗實例

3. 在 **「新項目」** 對話方塊中,按下 **「簡單專案**」 。節點。 **主控台應用程式**樣本應顯示在 **「樣本」 的視窗格中**。

4. 展開**簡單專案**節點。 應顯示**控制檯**子節點。 **簡單專案應用程式**樣本繼續顯示在 **「範本」** 窗格中。

5. 按下 **「取消並**停止調試」。

    ![簡單的專案匯總](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![簡單的專案主控台節點](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>取代項目樣本參數
- [創建基本項目系統,第1部分](../extensibility/creating-a-basic-project-system-part-1.md)展示了如何`ProjectNode.AddFileFromTemplate`覆蓋 方法,以進行一種基本的範本參數替換。 本節介紹如何使用更複雜的 Visual Studio 範本參數。

在 **「新建項目**」對話方塊中使用 Visual Studio 樣本建立專案時,樣本參數將替換為字串以自訂專案。 範本參數是一個特殊的權杖,以美元符號開始和結束,例如,$time$。 以下兩個參數對於在基於樣本的項目中啟用自訂特別有用:

- $GUID[1-10]$被新的Guid取代。 您最多可以指定 10 個唯一 GUID,例如,$guid 1 美元。

- $safeprojectname$是使用者在 **"新專案"** 對話方塊中提供的名稱,已修改以刪除所有不安全的字元和空格。

  如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。

### <a name="to-substitute-project-template-parameters"></a>取代項目樣本參數

1. 在*SimpleProjectNode.cs*檔案中,`AddFileFromTemplate`刪除方法 。

2. 在*\\樣本\專案\ConsoleApp_SimpleProject.myproj*檔中,\<找到 根命名空間>屬性並將其值更改為 $safeprojectname$。

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. 在*\\樣本_專案_簡單專案_程式.cs*檔案中,用以下代碼取代檔案的內容:

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

4. 重建簡單專案並開始調試。 應出現實驗實例。

5. 創建新的 SimpleProject 主控台應用程式。 (在 **"專案類型"** 窗格中,選擇 **「簡單專案**」。 在**視覺化工作室安裝的樣本**下,選擇**主控台應用程式**。

6. 在新建立的項目中,開啟*Program.cs*。 它的外觀應如下所示(檔中的 GUID 值會有所不同。

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

## <a name="create-a-project-property-page"></a>建立項目屬性頁
可以為項目類型創建屬性頁,以便使用者可以查看和更改基於範本的專案中的屬性。 本節介紹如何創建與配置無關的屬性頁。 此基本屬性頁使用屬性網格來顯示您在屬性頁類中公開的公共屬性。

從`SettingsPage`基類派生屬性頁類。 `SettingsPage`類提供的屬性網格知道大多數原始數據類型,並知道如何顯示它們。 此外,該`SettingsPage`類知道如何將屬性值保存到專案檔。

以在此部分建立的屬性頁,您可以變更並儲存以下項目屬性:

- AssemblyName

- OutputType

- 根命名空間。

1. 在*SimpleProjectPackage.cs*檔案中,將`ProvideObject`此屬性`SimpleProjectPackage`新增到 類別:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    這將屬性頁類`GeneralPropertyPage`與 COM 註冊。

2. SimpleProjectNode.cs*檔案*中,將這兩個重寫方法加入:`SimpleProjectNode`類別:

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

    這兩種方法都返回屬性頁 GUID 的陣列。 屬性頁 GUID 是陣列中的唯一元素,因此 **「屬性頁」** 對話框將僅顯示一個頁面。

3. 將名為*GeneralPropertyPage.cs*的類檔添加到 SimpleProject 專案中。

4. 使用以下代碼取代此檔案的內容:

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

    該`GeneralPropertyPage`類公開三個公共屬性"程式集名稱"、輸出類型和根命名空間。 由於 AssemblyName 沒有設定方法,因此它顯示為唯讀屬性。 輸出類型是枚舉常量,因此顯示為下拉清單。

    基`SettingsPage`類`ProjectMgr`提供 以保留屬性。 該方法`BindProperties``ProjectMgr`用於 檢索持久化屬性值並設置相應的屬性。 該方法`ApplyChanges``ProjectMgr`用於獲取屬性的值並將其保存到專案檔中。 屬性集方法設置為`IsDirty`true 以指示必須保留屬性。 保存專案或解決方案時會發生持久性。

5. 重建簡單專案解決方案並開始調試。 應出現實驗實例。

6. 在實驗實例中,創建新的 SimpleProject 應用程式。

7. Visual Studio 調用專案工廠,使用 Visual Studio 範本創建專案。 新的*Program.cs*檔案在代碼編輯器中打開。

8. 右鍵按下**解決方案資源管理員**中的項目節點,**然後按下屬性**。 [屬性頁面]**** 對話方塊隨即出現。

    ![簡單的項目屬性頁面](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>測試項目屬性頁
現在,您可以測試是否可以修改和更改屬性值。

1. 在**MyConsole 應用程式屬性頁**對話方塊中,將**預設命名空間**更改為 **「我的應用程式**」 。

2. 選擇**輸出類型屬性**,然後選擇**類別庫**。

3. 按一下 [套用]****，然後按一下 [確定]****。

4. 重新開啟 **「屬性頁」** 對話方塊,並驗證所做的更改是否已保留。

5. 關閉 Visual Studio 的實驗執行個體。

6. 重新打開實驗實例。

7. 重新開啟 **「屬性頁」** 對話方塊,並驗證所做的更改是否已保留。

8. 關閉 Visual Studio 的實驗執行個體。
    ![關閉實驗實體](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
