---
title: 逐步解說：使用專案範本建立網站資料行專案項目，第 2 部分 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79c27ec92d93f9f9cd88cc1155521b04ea7c2908
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868100"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>逐步解說：使用專案範本，第 2 部分建立網站資料行專案項目
  您定義自訂 SharePoint 專案項目類型，並將它與 Visual Studio 中的專案範本產生關聯之後，您也可以提供範本的精靈。 您可以使用精靈，在使用您的範本來建立新的專案，其中包含的專案項目時，從使用者收集資訊。 您所收集的資訊可以用來初始化專案項目中。

 在此逐步解說中，您會將精靈的網站欄專案範本所示[逐步解說：使用專案範本建立網站資料行專案項目，第 1 部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。 當使用者建立的網站欄專案時，精靈會收集站台資料行 （例如其基底類型和群組） 的相關資訊，並將這項資訊才能*Elements.xml*新專案中的檔案。

 本逐步解說將示範下列工作：

-   建立自訂 SharePoint 專案項目類型所關聯的專案範本的精靈。

-   定義自訂的精靈 UI，類似於 Visual Studio 中的 SharePoint 專案的內建精靈。

-   建立兩個*SharePoint 命令*，用來執行精靈時，呼叫本機 SharePoint 網站。 SharePoint 命令是可以用於 Visual Studio 擴充功能呼叫 SharePoint 伺服器物件模型中的 Api 的方法。 如需詳細資訊，請參閱 <<c0> [ 呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

-   您可以使用可置換的參數，初始化 SharePoint 專案檔，以您在精靈中所收集的資料。

-   每個新的網站欄專案執行個體中建立新的.snk 檔案。 這個檔案用來簽署專案輸出，讓 SharePoint 方案組件可以部署到全域組件快取。

-   偵錯和測試精靈。

> [!NOTE]
> 針對一系列的範例工作流程中，請參閱[SharePoint 工作流程範例](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples)。

## <a name="prerequisites"></a>必要條件
 若要執行本逐步解說中，您必須先建立 SiteColumnProjectItem 解決方案藉由完成[逐步解說：使用專案範本建立網站資料行專案項目，第 1 部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。

 您還需要完成這個逐步解說在開發電腦上的下列元件：

- 支援的 Windows、 SharePoint 和 Visual Studio 版本。

- Visual Studio SDK 中。 本逐步解說會使用**VSIX 專案**SDK 來建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識會很有幫助，但並非必要，若要完成本逐步解說：

- Visual Studio 中的專案和項目範本的精靈。 如需詳細資訊，請參閱[如何：使用精靈與專案範本](../extensibility/how-to-use-wizards-with-project-templates.md)而<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面。

- 在 SharePoint 中的網站資料行。 如需詳細資訊，請參閱 <<c0> [ 資料行](http://go.microsoft.com/fwlink/?LinkId=183547)。

## <a name="understand-the-wizard-components"></a>了解精靈元件
 在本逐步解說會示範 「 精靈 」 會包含數個元件。 下表說明這些元件。

|元件|描述|
|---------------|-----------------|
|精靈的實作|這是類別，名為`SiteColumnProjectWizard`，它會實作<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面。 這個介面會定義當精靈啟動和完成時，並在特定時間時精靈會執行 Visual Studio 會呼叫的方法。|
|精靈使用者介面|這是以 WPF 為基礎的視窗，名為`WizardWindow`。 此視窗包含兩個使用者控制項，名為`Page1`和`Page2`。 這些使用者控制項代表兩個在精靈的頁面。<br /><br /> 在本逐步解說，<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>精靈的實作方法會顯示精靈使用者介面。|
|精靈資料模型|這是中繼類別，名為`SiteColumnWizardModel`，以提供精靈使用者介面與精靈實作之間的層。 此範例會使用此類別協助抽象精靈的實作和彼此; 中的精靈 UI這個類別不是所有精靈的必要的元件。<br /><br /> 在此逐步解說中，精靈的實作會將傳遞`SiteColumnWizardModel`精靈視窗時，它會顯示精靈使用者介面的物件。 若要在 UI 中，儲存控制項的值，並執行工作，例如正在驗證輸入的網站 URL 有效，精靈 UI 就會使用此物件的方法。 使用者完成精靈之後，精靈的實作會使用`SiteColumnWizardModel`物件來判定 UI 的最終狀態。|
|專案簽章的經理|這是一個 helper 類別，名為`ProjectSigningManager`，這由精靈的實作每個新的專案執行個體中建立新的 key.snk 檔案。|
|SharePoint 命令|這些是用來執行精靈時，呼叫本機 SharePoint 網站的精靈資料模型的方法。 因為 SharePoint 命令必須以.NET Framework 3.5 為目標，這些命令會實作不同的組件與其餘的精靈程式碼。|

## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說中，您需要將數個專案加入至您在建立 SiteColumnProjectItem 方案[逐步解說：使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- WPF 專案。 您將實作<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面，並在此專案中定義的精靈 UI。

- 類別庫專案定義的 SharePoint 命令。 此專案必須以.net Framework 3.5 為目標。

  開始本逐步解說建立的專案。

#### <a name="to-create-the-wpf-project"></a>若要建立 WPF 專案

1.  在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，開啟 SiteColumnProjectItem 方案。

2.  中**方案總管**，開啟捷徑功能表**SiteColumnProjectItem**方案節點，選擇**新增**，然後選擇 **新專案**.

3.  在頂端**加入新的專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。

4.  依序展開**Visual C#** 節點或**Visual Basic**節點，然後選擇**Windows**節點。

5.  在專案範本清單中，選擇**WPF 使用者控制項程式庫**，將專案命名**ProjectTemplateWizard**，然後選擇**確定**  按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**ProjectTemplateWizard**專案加入方案，並開啟預設 UserControl1.xaml 檔案。

6.  從專案刪除 UserControl1.xaml 檔案。

#### <a name="to-create-the-sharepoint-commands-project"></a>若要建立 SharePoint 命令專案

1.  中**方案總管**，開啟 SiteColumnProjectItem 方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。

2.  在頂端**加入新的專案**對話方塊方塊中，選擇 **.NET Framework 3.5**清單中的.NET Framework 版本。

3.  依序展開**Visual C#**  節點或**Visual Basic**節點，然後選擇**Windows**節點。

4.  選擇**類別庫**專案範本，請將專案命名**SharePointCommands**，然後選擇**確定** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**SharePointCommands**專案加入方案，並開啟預設 Class1 的程式碼檔案。

5.  從專案刪除 Class1 的程式碼檔案。

## <a name="configure-the-projects"></a>將專案設定
 建立精靈之前，您必須新增一些程式碼檔案和專案的組件參考。

#### <a name="to-configure-the-wizard-project"></a>若要設定精靈專案

1.  在 **方案總管**，開啟捷徑功能表**ProjectTemplateWizard**專案節點，然後選擇**屬性**。

2.  在 **專案設計工具**，選擇**應用程式** 索引標籤，針對 Visual C# 專案或**編譯**Visual Basic 專案 索引標籤。

3.  請確定目標架構設為.NET Framework 4.5 中，而非.NET Framework 4.5 Client Profile。

     如需詳細資訊，請參閱[如何：以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

4.  開啟捷徑功能表**ProjectTemplateWizard**專案，選擇**新增**，然後選擇**新項目**。

5.  選擇**視窗 (WPF)** 項目，項目命名**WizardWindow**，然後選擇**新增** 按鈕。

6.  新增兩個**使用者控制項 (WPF)** 項目至專案，並將它們命名**Page1**並**Page2**。

7.  將四個程式碼檔案加入至專案，並提供下列名稱：

    -   SiteColumnProjectWizard

    -   SiteColumnWizardModel

    -   ProjectSigningManager

    -   CommandIds

8.  開啟捷徑功能表**ProjectTemplateWizard**專案節點，然後選擇**加入參考**。

9. 依序展開**組件**節點，選擇**延伸模組**節點，，然後選取下列組件旁邊的核取方塊：

    -   EnvDTE

    -   Microsoft.VisualStudio.OLE.Interop

    -   Microsoft.VisualStudio.SharePoint

    -   Microsoft.VisualStudio.Shell.11.0

    -   Microsoft.VisualStudio.Shell.Interop.10.0

    -   Microsoft.VisualStudio.Shell.Interop.11.0

    -   Microsoft.VisualStudio.TemplateWizardInterface

10. 選擇**確定**按鈕以新增至專案的組件。

11. 在**方案總管**下方**參考**資料夾**ProjectTemplateWizard**專案中，選擇**EnvDTE**。

12. 在 [**屬性**] 視窗中，變更的值**內嵌 Interop 類型**屬性設**False**。

13. 如果您正在開發 Visual Basic 專案，使用匯入 ProjectTemplateWizard 命名空間到您的專案**專案設計工具**。

     如需詳細資訊，請參閱[如何：新增或移除匯入命名空間&#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)。

#### <a name="to-configure-the-sharepointcommands-project"></a>若要設定 SharePointcommands 專案

1.  在 **方案總管**，選擇**SharePointCommands**專案節點。

2.  在功能表列上選擇 **專案**，**加入現有項目**。

3.  在 [**加入現有項目**] 對話方塊中，瀏覽至包含 ProjectTemplateWizard 專案中，程式碼檔案的資料夾，然後選擇**CommandIds**程式碼檔案。

4.  選擇箭號旁**新增**按鈕，然後再選擇**加入做為連結**上出現的功能表選項。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增的程式碼檔案**SharePointCommands**專案做為連結。 程式碼檔案位於**ProjectTemplateWizard**中的專案，但檔案中的程式碼也編譯**SharePointCommands**專案。

5.  在  **SharePointCommands**專案中，加入另一個名為命令的程式碼檔案。

6.  選擇 SharePointCommands 專案，，然後在功能表列上選擇 **專案** > **加入參考**。

7.  依序展開**組件**節點，選擇**延伸模組**節點，，然後選取下列組件旁邊的核取方塊：

    -   Microsoft.SharePoint

    -   Microsoft.VisualStudio.SharePoint.Commands

8.  選擇**確定**按鈕以新增至專案的組件。

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>建立精靈模型、 簽章管理員和 SharePoint 的命令 Id
 將程式碼加入 ProjectTemplateWizard 專案範例中實作下列元件：

- SharePoint 命令識別碼。 這些字串會識別精靈會使用 SharePoint 命令。 稍後在本逐步解說中，您會加入至 SharePointCommands 專案，以實作命令的程式碼。

- 精靈資料模型。

- 專案的簽章管理員。

  如需有關這些元件的詳細資訊，請參閱 <<c0> [ 了解精靈元件](#understand-the-wizard-components)。

#### <a name="to-define-the-sharepoint-command-ids"></a>若要定義的 SharePoint 命令識別碼

1.  在 ProjectTemplateWizard 專案中，開啟 CommandIds 程式碼檔案，並再將此檔案的整個內容取代下列程式碼。

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>若要建立精靈模型

1.  開啟 SiteColumnWizardModel 程式碼檔案，並以下列程式碼取代此檔案的整個內容。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>若要建立專案的簽章管理員

1.  開啟 ProjectSigningManager 程式碼檔案，然後將此檔案的整個內容取代為下列的程式碼，

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>建立精靈使用者介面
 新增 XAML 來定義精靈 視窗和精靈頁面，提供 UI 的兩個使用者控制項的 UI，並加入程式碼來定義 「 視窗 」 和 「 使用者控制項的行為。 您所建立的精靈，類似於 Visual Studio 中的 SharePoint 專案的內建精靈。

> [!NOTE]
>  在下列步驟中，您將 XAML 或程式碼新增至您的專案之後您的專案時，會有某些編譯錯誤。 當您在稍後步驟中加入程式碼時，這些錯誤就會消失運作。

#### <a name="to-create-the-wizard-window-ui"></a>若要建立 UI 中的 [精靈] 視窗

1.  在 ProjectTemplateWizard 專案中，開啟 WizardWindow.xaml 檔案的捷徑功能表，然後再選擇**開啟**設計工具中開啟的視窗。

2.  在設計工具的 [XAML] 檢視中，請以下列 XAML 取代目前的 XAML。 XAML 定義 UI，其中包含標題， <xref:System.Windows.Controls.Grid> ，其中包含的精靈頁面和導覽按鈕的視窗的底部。

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    >  在此 XAML 中建立的視窗衍生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>基底類別。 當您將自訂的 WPF 對話方塊加入 Visual Studio 時，我們建議您從有一致的樣式，與其他 Visual Studio 對話方塊，並避免強制回應對話方塊的問題可能會發生這個類別衍生您的對話方塊。 如需詳細資訊，請參閱 <<c0> [ 建立和管理強制回應對話方塊](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)。

3.  如果您正在開發 Visual Basic 專案，移除`ProjectTemplateWizard`來自命名空間`WizardWindow`中的類別名稱`x:Class`屬性`Window`項目。 此元素會在第一行中的 XAML。 當您完成時，第一個行看起來應該如下列範例所示。

    ```xml
    <Window x:Class="WizardWindow"
    ```

4.  開啟 WizardWindow.xaml 檔案的程式碼後置檔案。

5.  這個檔案的內容取代除了`using`宣告上方的檔案，以下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>若要建立第一個精靈頁面 UI

1.  在 ProjectTemplateWizard 專案中，開啟 Page1.xaml 檔案的捷徑功能表，然後再選擇**開啟**設計工具中開啟使用者控制項。

2.  在設計工具的 [XAML] 檢視中，請以下列 XAML 取代目前的 XAML。 XAML 定義 UI，其中包含使用者可以在其中輸入他們想要用於偵錯的本機網站 URL 文字方塊。 UI 也包含讓使用者可以指定專案是否已沙箱化的選項按鈕。

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3.  如果您正在開發 Visual Basic 專案，移除`ProjectTemplateWizard`來自命名空間`Page1`中的類別名稱`x:Class`屬性`UserControl`項目。 這是在第一行中的 XAML。 當您完成時的第一行看起來應該如下所示。

    ```xml
    <UserControl x:Class="Page1"
    ```

4.  取代檔案的內容 Page1.xaml，除了`using`宣告上方的檔案，以下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>若要建立第二個精靈頁面 UI

1.  在 ProjectTemplateWizard 專案中，開啟 Page2.xaml 檔案的捷徑功能表，然後再選擇**開啟**。

     使用者控制項隨即在設計工具中開啟。

2.  在 XAML 檢視中，請以下列 XAML 取代目前的 XAML。 XAML 會定義包含下拉式清單選擇 網站資料行、 指定要用來顯示網站資料行在圖庫中，內建或自訂群組的下拉式方塊和文字方塊，用於指定的網站資料行名稱的基底類型的 UI。

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3.  如果您正在開發 Visual Basic 專案，移除`ProjectTemplateWizard`來自命名空間`Page2`中的類別名稱`x:Class`屬性`UserControl`項目。 這是在第一行中的 XAML。 當您完成時的第一行看起來應該如下所示。

    ```xml
    <UserControl x:Class="Page2"
    ```

4.  Page2.xaml 檔案的程式碼後置檔案的內容取代除了`using`宣告上方的檔案，以下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>實作精靈
 藉由實作定義精靈 的主要功能<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面。 這個介面會定義當精靈啟動和完成時，並在特定時間時精靈會執行 Visual Studio 會呼叫的方法。

#### <a name="to-implement-the-wizard"></a>若要實作精靈

1.  在 ProjectTemplateWizard 專案中，開啟 SiteColumnProjectWizard 程式碼檔案。

2.  此檔案的整個內容取代為下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>建立 SharePoint 命令
 建立兩個呼叫 SharePoint 伺服器物件模型的自訂命令。 一個命令會判斷是否為有效的使用者類型在精靈中的網站 URL。 另一個命令會取得所有的欄位型別從指定的 SharePoint 網站，讓使用者可以選取要作為其新的網站欄的基礎。

#### <a name="to-define-the-sharepoint-commands"></a>若要定義的 SharePoint 命令

1.  在  **SharePointCommands**專案中，開啟指令碼檔案。

2.  此檔案的整個內容取代為下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>檢查點
 此時在逐步解說中，精靈的所有程式碼現在是在專案中。 建置專案，以確定它會編譯無誤。

#### <a name="to-build-your-project"></a>建置您的專案

1.  在功能表列上選擇 [建置] > [建置解決方案]。

## <a name="removing-the-keysnk-file-from-the-project-template"></a>移除專案範本中的 key.snk 檔案
 在 [逐步解說：使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)，您所建立的專案範本包含用來簽署每個網站欄專案執行個體的 key.snk 檔案。 這個 key.snk 檔案不再是必要的因為精靈現在會產生新的 key.snk 檔案，每個專案。 移除專案範本中的 key.snk 檔案，並移除此檔案的參考。

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>若要移除的專案範本中的 key.snk 檔案

1.  中**方案總管**下方**SiteColumnProjectTemplate**節點，開啟捷徑功能表**key.snk**檔案，然後再選擇 **刪除**.

2.  在出現確認對話方塊中，選擇**確定** 按鈕。

3.  底下**SiteColumnProjectTemplate**節點，開啟 SiteColumnProjectTemplate.vstemplate 檔案，然後再從中移除下列項目。

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4.  儲存並關閉檔案。

5.  底下**SiteColumnProjectTemplate**節點，開啟 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 檔案，然後再移除下列`PropertyGroup`從它的項目。

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6.  移除下列`None`項目。

    ```xml
    <None Include="key.snk" />
    ```

7.  儲存並關閉檔案。

## <a name="associating-the-wizard-with-the-project-template"></a>關聯的專案範本的精靈
 既然您已實作 「 精靈 」，您必須建立關聯精靈**站台的資料行**專案範本。 有三個程序，您必須完成才能執行這項操作：

1.  精靈組件，以強式名稱簽署。

2.  取得精靈的組件的公開金鑰語彙基元。

3.  在.vstemplate 檔案中新增精靈 的組件的參考**站台的資料行**專案範本。

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>若要簽署以強式名稱的組件精靈

1.  在 [**方案總管] 中**，開啟捷徑功能表**ProjectTemplateWizard**專案，，然後選擇**屬性**。

2.  在  **Signing**索引標籤上，選取**簽署組件**核取方塊。

3.  在 **選擇強式名稱金鑰檔**清單中，選擇**\<新增...>**。

4.  中**建立強式名稱金鑰**對話方塊方塊中，輸入新的金鑰檔的名稱清除**保護我的金鑰檔使用密碼**核取方塊，，然後選擇 [**確定**] 按鈕。

5.  開啟捷徑功能表**ProjectTemplateWizard**專案，，然後選擇**建置**建立 ProjectTemplateWizard.dll 檔案。

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>若要取得的公開金鑰權杖精靈組件

1.  在上**開始 功能表**，選擇**所有程式**，選擇  **Microsoft Visual Studio**，選擇**Visual Studio Tools**，然後選擇  **開發人員命令提示字元**。

     Visual Studio 命令提示字元 視窗隨即開啟。

2.  執行下列命令，取代*PathToWizardAssembly* ProjectTemplateWizard 專案到開發電腦上建置的 ProjectTemplateWizard.dll 組件的完整路徑：

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Visual Studio 命令提示字元 視窗會寫入 ProjectTemplateWizard.dll 組件的公開金鑰 token。

3.  Visual Studio 命令提示字元視窗保持開啟。 您將在下一個程序期間需要的公開金鑰 token。

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>將.vstemplate 檔案中的精靈組件的參考

1.  在 **方案總管**，展開**SiteColumnProjectTemplate**專案節點，然後開啟 SiteColumnProjectTemplate.vstemplate 檔案。

2.  接近檔案結尾，新增下列`WizardExtension`之間的項目`</TemplateContent>`和`</VSTemplate>`標記。 取代*您的語彙基元*的值`PublicKeyToken`屬性與您在上一個程序中取得的公開金鑰 token。

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     如需詳細資訊`WizardExtension`項目，請參閱 < [WizardExtension 項目&#40;Visual Studio 範本&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates)。

3.  儲存並關閉檔案。

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>可置換的參數加入 Elements.xml 檔案中的專案範本
 加入數個可取代的參數，以便*Elements.xml* SiteColumnProjectTemplate 專案檔中的。 這些參數會初始化`RunStarted`方法中的`SiteColumnProjectWizard`您稍早定義的類別。 當使用者建立的網站欄專案時，Visual Studio 會自動取代這些參數*Elements.xml*檔案在新的專案，在精靈中指定的值。

 可置換的參數為開頭和結尾的貨幣符號 （$） 字元的語彙基元。 除了定義您自己可置換的參數，您可以使用內建的參數，定義及初始化 SharePoint 專案系統。 如需詳細資訊，請參閱 <<c0> [ 可置換的參數](../sharepoint/replaceable-parameters.md)。

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>若要加入 Elements.xml 檔案中的可置換的參數

1.  在 SiteColumnProjectTemplate 專案中的內容取代*Elements.xml*以下列 XML 檔案。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     新的 XML 變更的值`Name`， `DisplayName`， `Type`，和`Group`屬性加入自訂可置換的參數。

2.  儲存並關閉檔案。

## <a name="add-the-wizard-to-the-vsix-package"></a>將精靈加入至 VSIX 封裝
 若要部署精靈，並包含網站欄專案範本的 VSIX 封裝，請將精靈專案和 SharePoint 命令專案的參考加入 source.extension.vsixmanifest 檔案中，在 VSIX 專案。

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>若要將精靈加入至 VSIX 封裝

1.  在 **方案總管**，請在**SiteColumnProjectItem**專案中，開啟捷徑功能表**source.extension.vsixmanifest**檔案，然後再選擇  **開啟**。

     Visual Studio 會在資訊清單編輯器中開啟檔案。

2.  上**資產**索引標籤的 編輯器 中，選擇**新增** 按鈕。

     **加入新資產**對話方塊隨即開啟。

3.  在 **型別**清單中，選擇**Microsoft.VisualStudio.Assembly**。

4.  在 **來源**清單中，選擇**目前方案中的專案**。

5.  在 [**專案**清單中，選擇**ProjectTemplateWizard**，然後選擇 **[確定]** ] 按鈕。

6.  上**資產**索引標籤的 [編輯器] 中，選擇**新增**按鈕一次。

     **加入新資產**對話方塊隨即開啟。

7.  在 **型別**清單中，輸入**SharePoint.Commands.v4**。

8.  在 **來源**清單中，選擇**目前方案中的專案**。

9. 在 **專案**清單中，選擇**SharePointCommands**專案，，然後選擇**確定**按鈕。

10. 在功能表列上選擇 **建置** > **建置方案**，然後確認方案建置無誤。

## <a name="test-the-wizard"></a>測試精靈
 您現在已準備好測試精靈。 首先，啟動偵錯 SiteColumnProjectItem 方案在 Visual Studio 的實驗執行個體。 然後，在 Visual Studio 的實驗執行個體中測試的網站欄專案的精靈。 最後，建置並執行專案，以確認站台的資料行可以正常運作。

#### <a name="to-start-debugging-the-solution"></a>若要啟動偵錯方案

1.  使用系統管理認證，重新啟動 Visual Studio，然後開啟 SiteColumnProjectItem 解決方案。

2.  在 ProjectTemplateWizard 專案中，開啟 SiteColumnProjectWizard 程式碼檔案，然後加入中斷點至第一行中的程式碼`RunStarted`方法。

3.  在功能表列上選擇 **偵錯** > **例外狀況**。

4.  在**例外狀況**對話方塊方塊中，請確定**擲回**並**使用者未處理**核取方塊**Common Language Runtime 例外狀況**會先清除，，然後選擇 [ **[確定]** ] 按鈕。

5.  開始偵錯選擇**F5**金鑰或，功能表列選擇**偵錯** > **開始偵錯**。

     Visual Studio 會 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 安裝擴充功能，並啟動 Visual Studio 的實驗執行個體。 在 Visual Studio 這個執行個體中，您將測試專案項目。

#### <a name="to-test-the-wizard-in-visual-studio"></a>若要在 Visual Studio 中測試精靈

1. 在實驗性 Visual Studio 執行個體，在功能表列上，選擇**檔案** > **新增** > **專案**。

2. 依序展開**Visual C#** 節點或**Visual Basic**節點 （取決於您的專案範本支援語言），展開**SharePoint** ] 節點，然後選擇 [**2010年**節點。

3. 在專案範本清單中，選擇**網站資料行**，將專案命名為**SiteColumnWizardTest**，然後選擇**確定**  按鈕。

4. 確認 Visual Studio 的其他執行個體中的程式碼是在您稍早在設定的中斷點上停止`RunStarted`方法。

5. 繼續偵錯專案，選擇**F5**金鑰或，功能表列選擇**偵錯** > **繼續**。

6. 在  **SharePoint 自訂精靈**，輸入您想要用於偵錯時，網站的 URL，然後選擇**下一步**  按鈕。

7. 中的第二頁**SharePoint 自訂精靈**，進行下列選擇：

   - 在 **型別**清單中，選擇**布林**。

   - 在 **群組**清單中，選擇**自訂/否資料行**。

   - 在**名稱**方塊中，輸入**My/否資料行**，然後選擇**完成** 按鈕。

     中**方案總管**，新的專案隨即出現，並包含名為專案項目的**Field1**，和 Visual Studio 開啟的專案*Elements.xml*在編輯器中的檔案。

8. 確認*Elements.xml*包含您在精靈中指定的值。

#### <a name="to-test-the-site-column-in-sharepoint"></a>若要在 SharePoint 中測試網站資料行

1.  在 Visual Studio 的實驗性執行個體，選擇**F5**索引鍵。

     網站資料行是封裝並部署至 SharePoint 網站**網站 URL**指定專案屬性。 Web 瀏覽器中開啟此站台的預設頁面。

    > [!NOTE]
    >  如果**指令碼偵錯已停用** 對話方塊出現時，選擇**是**按鈕以繼續進行偵錯專案。

2.  在上**站台動作**功能表上，選擇**站台設定**。

3.  在站台設定 頁面下**資源庫**，選擇**站台的資料行**連結。

4.  在站台的資料行清單中，確認**自訂/否資料行**群組中包含名為的資料行**My/否資料行**，然後關閉網頁瀏覽器。

## <a name="clean-up-the-development-computer"></a>清除開發電腦
 完成測試的專案項目之後，請從 Visual Studio 的實驗執行個體中移除專案範本。

#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦

1.  在實驗性 Visual Studio 執行個體，在功能表列上，選擇**工具** > **擴充功能和更新**。

     [擴充功能和更新] 對話方塊隨即開啟。

2.  在延伸模組清單中，選擇**站台的資料行**，然後選擇**解除安裝** 按鈕。

3.  在出現的對話方塊中，選擇 **[是]** 按鈕，以確認您要解除安裝延伸模組，然後選擇**立即重新啟動**按鈕以完成解除安裝。

4.  關閉 Visual Studio 的實驗執行個體和 CustomActionProjectItem 方案已開啟的執行個體。

     如需如何部署[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]延伸模組，請參閱[運送 Visual Studio 擴充功能](/visualstudio/extensibility/shipping-visual-studio-extensions)。

## <a name="see-also"></a>另請參閱
- [逐步解說：使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [為 SharePoint 專案項目建立項目範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 範本結構描述參考](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [如何：使用精靈與專案範本](../extensibility/how-to-use-wizards-with-project-templates.md)
