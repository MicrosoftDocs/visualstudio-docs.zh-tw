---
title: 使用專案範本建立網站資料行專案專案（第2部分）
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
ms.openlocfilehash: 9e53cc877a4e462a458f3bfd455ed222c3b2e17b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984676"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>逐步解說：使用專案範本建立網站資料行專案專案（第2部分）
  在您定義 SharePoint 專案專案的自訂類型，並將它與 Visual Studio 中的專案範本產生關聯之後，您可能也會想要為範本提供 wizard。 當使用者使用您的範本來建立包含專案專案的新專案時，您可以使用 wizard 來收集他們的資訊。 您收集的資訊可以用來初始化專案專案。

 在此逐步解說中，您將會在 [[逐步解說：使用專案範本建立網站資料行專案專案] （第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)中示範的網站資料行專案範本中加入 wizard。 當使用者建立網站資料行專案時，嚮導會收集網站資料行（例如其基底類型和群組）的相關資訊，並將這項資訊新增至新專案中的*元素 .xml*檔案。

 本逐步解說將示範下列工作：

- 建立與專案範本相關聯之自訂 SharePoint 專案專案類型的 wizard。

- 定義自訂的 wizard UI，類似于 Visual Studio 中 SharePoint 專案的內建嚮導。

- 建立兩個*SharePoint 命令*，在嚮導執行時用來呼叫本機 SharePoint 網站。 SharePoint 命令是 Visual Studio 擴充功能在 SharePoint 伺服器物件模型中呼叫 Api 所使用的方法。 如需詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

- 使用可取代的參數，以您在嚮導中收集的資料來初始化 SharePoint 專案檔案。

- 在每個新的網站資料行專案實例中建立新的 .snk 檔案。 這個檔案是用來簽署專案輸出，因此 SharePoint 方案元件可以部署到全域組件快取。

- 調試和測試 wizard。

> [!NOTE]
> 如需一系列範例工作流程，請參閱[SharePoint 工作流程範例](/sharepoint/dev/general-development/sharepoint-workflow-samples)。

## <a name="prerequisites"></a>Prerequisites
 若要執行此逐步解說，您必須先完成逐步解說[：使用專案範本建立網站資料行專案專案（第1部分），](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)以建立 SiteColumnProjectItem 解決方案。

 您也需要在開發電腦上有下列元件，才能完成此逐步解說：

- 支援的 Windows、SharePoint 和 Visual Studio 版本。

- Visual Studio SDK。 本逐步解說會使用 SDK 中的**Vsix 專案**範本來建立 vsix 封裝，以部署專案專案。 如需詳細資訊，請參閱[Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成逐步解說：

- Visual Studio 中的專案和專案範本的嚮導。 如需詳細資訊，請參閱[如何：使用含有專案範本](../extensibility/how-to-use-wizards-with-project-templates.md)和 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面的嚮導。

- SharePoint 中的網站資料行。 如需詳細資訊，請參閱資料[行](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))。

## <a name="understand-the-wizard-components"></a>瞭解 wizard 元件
 本逐步解說中示範的 wizard 包含數個元件。 下表描述這些元件。

|元件|描述|
|---------------|-----------------|
|Wizard 的執行|這是一個名為 `SiteColumnProjectWizard`的類別，它會執行 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面。 這個介面會定義當 wizard 開始並完成時，以及在執行 wizard 的特定時間，Visual Studio 呼叫的方法。|
|Wizard UI|這是以 WPF 為基礎的視窗，名為 `WizardWindow`。 此視窗包含兩個名為 `Page1` 和 `Page2`的使用者控制項。 這些使用者控制項代表 wizard 的兩頁。<br /><br /> 在此逐步解說中，「wizard」執行的 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法會顯示 wizard UI。|
|Wizard 資料模型|這是名為 `SiteColumnWizardModel`的中繼類別，它會在 wizard UI 與 wizard 的執行之間提供一層。 這個範例會使用此類別來協助讓 wizard 的執行和 wizard UI 彼此的抽象化。這個類別不是所有嚮導的必要元件。<br /><br /> 在此逐步解說中，wizard 的執行會在顯示 wizard UI 時，將 `SiteColumnWizardModel` 物件傳遞至 wizard 視窗。 Wizard UI 會使用這個物件的方法，將控制項的值儲存在 UI 中，以及執行諸如驗證輸入網站 URL 是否有效等工作。 在使用者完成 wizard 之後，嚮導的執行會使用 `SiteColumnWizardModel` 物件來判斷 UI 的最終狀態。|
|專案簽署管理員|這是名為 `ProjectSigningManager`的 helper 類別，可供 wizard 執行用來在每個新的專案實例中建立新的金鑰 .snk 檔案。|
|SharePoint 命令|這些是 wizard 資料模型在執行 wizard 時，用來呼叫本機 SharePoint 網站的方法。 因為 SharePoint 命令必須將目標設為 .NET Framework 3.5，所以這些命令會在與其余的 wizard 程式碼不同的元件中執行。|

## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說，您需要將數個專案加入至您在逐步解說[：使用專案範本建立網站資料行專案專案](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)中所建立的 SiteColumnProjectItem 方案，第1部分：

- WPF 專案。 您將會執行 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面，並在此專案中定義 wizard UI。

- 定義 SharePoint 命令的類別庫專案。 此專案必須以 the.NET Framework 3.5 為目標。

  藉由建立專案來啟動逐步解說。

#### <a name="to-create-the-wpf-project"></a>若要建立 WPF 專案

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，開啟 SiteColumnProjectItem 方案。

2. 在**方案總管**中，開啟 [ **SiteColumnProjectItem**方案] 節點的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增專案**]。

3. 在 [**加入新的專案**] 對話方塊的頂端，確定已在 .NET Framework 版本清單中選擇 [ **.NET Framework 4.5** ]。

4. 展開 [**視覺C#效果**] 節點或 [ **Visual Basic** ] 節點，然後選擇 [ **Windows** ] 節點。

5. 在專案範本清單中，選擇 [ **WPF 使用者控制項程式庫**]，將專案命名為**ProjectTemplateWizard**，然後選擇 [**確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將**ProjectTemplateWizard**專案新增至方案，並開啟預設的 UserControl1. xaml 檔案。

6. 刪除專案中的 UserControl1。

#### <a name="to-create-the-sharepoint-commands-project"></a>若要建立 SharePoint 命令專案

1. 在**方案總管**中，開啟 [SiteColumnProjectItem 方案] 節點的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增專案**]。

2. 在 [**加入新的專案**] 對話方塊的頂端，選擇 .NET Framework 版本清單中的 [ **.NET Framework 3.5** ]。

3. 展開 [**視覺C#效果**] 節點或 [ **Visual Basic** ] 節點，然後選擇 [ **Windows** ] 節點。

4. 選擇 [**類別庫**] 專案範本，將專案命名為**SharePointCommands**，然後選擇 [**確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將**SharePointCommands**專案新增至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-projects"></a>設定專案
 建立嚮導之前，您必須先將一些程式碼檔案和元件參考加入至專案。

#### <a name="to-configure-the-wizard-project"></a>若要設定 wizard 專案

1. 在**方案總管**中，開啟**ProjectTemplateWizard**專案節點的快捷方式功能表，然後選擇 [**屬性**]。

2. 在 [**專案設計**工具] 中，選擇視覺C#專案的 [**應用程式**] 索引標籤或 Visual Basic 專案的 [**編譯**] 索引標籤。

3. 請確定 目標 framework 設定為 .NET Framework 4.5，而不是 .NET Framework 4.5 用戶端設定檔。

     如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

4. 開啟**ProjectTemplateWizard**專案的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增專案**]。

5. 選擇 [**視窗（WPF）]** 專案，將專案命名為**WizardWindow**，然後選擇 [**新增**] 按鈕。

6. 將兩個**使用者控制項（WPF）** 專案新增至專案，並將其命名為**Page1**和**Page2**。

7. 將四個程式碼檔案新增至專案，並為其指定下列名稱：

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. 開啟**ProjectTemplateWizard**專案節點的快捷方式功能表，然後選擇 [**加入參考**]。

9. 展開 [**元件**] 節點，選擇 [**擴充**功能] 節點，然後選取下列元件旁的核取方塊：

    - EnvDTE

    - VisualStudio. Interop

    - VisualStudio. SharePoint

    - VisualStudio。

    - VisualStudio. Shell。

    - VisualStudio. Shell。

    - Microsoft.VisualStudio.TemplateWizardInterface

10. 選擇 [**確定]** 按鈕，將元件加入至專案。

11. 在**方案總管**中，在**ProjectTemplateWizard**專案的 [**參考**] 資料夾底下，選擇 [ **EnvDTE**]。

12. 在 [**屬性**] 視窗中，將 [**內嵌 Interop 類型**] 屬性的值變更為**False**。

13. 如果您正在開發 Visual Basic 專案，請使用 [**專案設計**工具] 將 ProjectTemplateWizard 命名空間匯入您的專案中。

     如需詳細資訊，請參閱[如何：新增或移除匯&#40;入&#41;的命名空間 Visual Basic](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)。

#### <a name="to-configure-the-sharepointcommands-project"></a>若要設定 SharePointcommands 專案

1. 在**方案總管**中，選擇 [ **SharePointCommands** ] 專案節點。

2. 在功能表列上，選擇 [**專案**]、[**加入現有專案**]。

3. 在 [**加入現有專案**] 對話方塊中，流覽至包含 ProjectTemplateWizard 專案之程式碼檔案的資料夾，然後選擇 [ **CommandIds** ] 程式碼檔案。

4. 選擇 [**新增**] 按鈕旁邊的箭號，然後在出現的功能表上選擇 [**加入為連結**] 選項。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將程式碼檔案新增至**SharePointCommands**專案，做為連結。 程式碼檔案位於**ProjectTemplateWizard**專案中，但檔案中的程式碼也會在**SharePointCommands**專案中進行編譯。

5. 在**SharePointCommands**專案中，新增另一個名為命令的程式碼檔案。

6. 選擇 [SharePointCommands] 專案，然後在功能表列上選擇 [**專案**] > [**加入參考**]。

7. 展開 [**元件**] 節點，選擇 [**擴充**功能] 節點，然後選取下列元件旁的核取方塊：

    - Microsoft SharePoint

    - VisualStudio 的命令

8. 選擇 [**確定]** 按鈕，將元件加入至專案。

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>建立嚮導模型、簽署管理員和 SharePoint 命令識別碼
 將程式碼新增至 ProjectTemplateWizard 專案，以在範例中執行下列元件：

- SharePoint 命令識別碼。 這些字串會識別 wizard 使用的 SharePoint 命令。 稍後在本逐步解說中，您會將程式碼加入至 SharePointCommands 專案來執行命令。

- Wizard 資料模型。

- 專案簽署管理員。

  如需這些元件的詳細資訊，請參閱[瞭解 wizard 元件](#understand-the-wizard-components)。

#### <a name="to-define-the-sharepoint-command-ids"></a>若要定義 SharePoint 命令識別碼

1. 在 ProjectTemplateWizard 專案中，開啟 CommandIds 程式碼檔案，然後以下列程式碼取代此檔案的整個內容。

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>建立嚮導模型

1. 開啟 SiteColumnWizardModel 程式碼檔案，並以下列程式碼取代此檔案的整個內容。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>若要建立專案簽署管理員

1. 開啟 ProjectSigningManager 程式碼檔案，然後將這個檔案的整個內容取代為下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>建立 wizard UI
 新增 XAML 以定義 wizard 視窗的 UI，以及提供 wizard 頁面 UI 的兩個使用者控制項，並加入程式碼來定義視窗和使用者控制項的行為。 您建立的 wizard 與 Visual Studio 中 SharePoint 專案的內建 wizard 類似。

> [!NOTE]
> 在下列步驟中，當您將 XAML 或程式碼加入至專案之後，您的專案將會有一些編譯錯誤。 當您在稍後的步驟中新增程式碼時，這些錯誤就會消失。

#### <a name="to-create-the-wizard-window-ui"></a>建立嚮導視窗 UI

1. 在 ProjectTemplateWizard 專案中，開啟 WizardWindow 檔案的快捷方式功能表，然後選擇 [**開啟**] 以在設計工具中開啟視窗。

2. 在設計工具的 XAML 視圖中，以下列 XAML 取代目前的 XAML。 XAML 會定義一個 UI，其中包含標題、包含 wizard 頁面的 <xref:System.Windows.Controls.Grid>，以及視窗底部的導覽按鈕。

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > 在此 XAML 中建立的視窗衍生自 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 的基類。 當您將自訂 WPF 對話方塊新增至 Visual Studio 時，建議您從這個類別衍生對話方塊，使其與其他 Visual Studio 對話方塊具有一致的樣式，以及避免可能發生的強制回應對話方塊問題。 如需詳細資訊，請參閱[建立和管理模式對話方塊](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)。

3. 如果您正在開發 Visual Basic 專案，請在 `Window` 元素的 `x:Class` 屬性中，從 `WizardWindow` 類別名稱中移除 `ProjectTemplateWizard` 命名空間。 這個元素位於 XAML 的第一行。 當您完成時，第一行看起來應該如下列範例所示。

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. 開啟 WizardWindow 檔的程式碼後置檔案。

5. 以下列程式碼取代此檔案的內容，但不包括檔案頂端的 `using` 宣告。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>建立第一個 wizard 頁面 UI

1. 在 ProjectTemplateWizard 專案中，開啟 Page1. xaml 檔案的快捷方式功能表，然後選擇 [**開啟**] 以在設計工具中開啟使用者控制項。

2. 在設計工具的 XAML 視圖中，以下列 XAML 取代目前的 XAML。 XAML 會定義一個 UI，其中包含一個文字方塊，使用者可以在其中輸入要用來進行偵錯工具的本機網站 URL。 UI 也包含選項按鈕，使用者可以用來指定專案是否已沙箱化。

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. 如果您正在開發 Visual Basic 專案，請在 `UserControl` 元素的 `x:Class` 屬性中，從 `Page1` 類別名稱中移除 `ProjectTemplateWizard` 命名空間。 這是在 XAML 的第一行。 當您完成時，第一行看起來應該如下所示。

    ```xml
    <UserControl x:Class="Page1"
    ```

4. 將 Page1. xaml 檔案的內容取代為檔案頂端的 `using` 宣告，但使用下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>若要建立第二個 wizard page UI

1. 在 ProjectTemplateWizard 專案中，開啟 Page2 檔案的快捷方式功能表，然後選擇 [**開啟**]。

     使用者控制項隨即在設計工具中開啟。

2. 在 XAML 視圖中，以下列 XAML 取代目前的 XAML。 XAML 會定義一個 UI，其中包含選擇 [網站] 資料行之基底類型的下拉式清單、用來指定內建或自訂群組（用來在資源庫中顯示 [網站] 資料行）的下拉式方塊，以及用來指定網站資料行名稱的文字方塊。

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. 如果您正在開發 Visual Basic 專案，請在 `UserControl` 元素的 `x:Class` 屬性中，從 `Page2` 類別名稱中移除 `ProjectTemplateWizard` 命名空間。 這是在 XAML 的第一行。 當您完成時，第一行看起來應該如下所示。

    ```xml
    <UserControl x:Class="Page2"
    ```

4. 以下列程式碼取代 Page2 檔案的程式碼後置檔案內容，但檔案頂端的 `using` 宣告除外。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>執行嚮導
 藉由執行 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面來定義 wizard 的主要功能。 這個介面會定義當 wizard 開始並完成時，以及在執行 wizard 的特定時間，Visual Studio 呼叫的方法。

#### <a name="to-implement-the-wizard"></a>若要執行 wizard

1. 在 ProjectTemplateWizard 專案中，開啟 SiteColumnProjectWizard 程式碼檔案。

2. 將此檔案的整個內容取代為下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>建立 SharePoint 命令
 建立兩個呼叫 SharePoint 伺服器物件模型的自訂命令。 其中一個命令會判斷使用者在 wizard 中鍵入的網站 URL 是否有效。 另一個命令會從指定的 SharePoint 網站取得所有欄位類型，讓使用者可以選取要使用哪一個做為新網站資料行的基礎。

#### <a name="to-define-the-sharepoint-commands"></a>若要定義 SharePoint 命令

1. 在**SharePointCommands**專案中，開啟命令程式碼檔案。

2. 將此檔案的整個內容取代為下列程式碼。

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>檢查點
 在本逐步解說的這個階段中，wizard 的所有程式碼現在都在專案中。 建立專案，以確保它會編譯而不會發生錯誤。

#### <a name="to-build-your-project"></a>建置您的專案

1. 在功能表列上選擇 [建置] > [建置解決方案]。

## <a name="removing-the-keysnk-file-from-the-project-template"></a>從專案範本移除金鑰 .snk 檔案
 在[逐步解說：使用專案範本建立網站資料行專案專案（第1部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)）中，您所建立的專案範本包含用來簽署每個網站資料行專案實例的金鑰 .snk 檔案。 這個金鑰 .snk 檔案已不再需要，因為 wizard 現在會針對每個專案產生新的金鑰 .snk 檔案。 從專案範本移除金鑰 .snk 檔案，並移除此檔案的參考。

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>若要從專案範本移除金鑰 .snk 檔案

1. 在**方案總管**的 [ **SiteColumnProjectTemplate** ] 節點下，開啟 [**金鑰 .snk** ] 檔案的快捷方式功能表，然後選擇 [**刪除**]。

2. 在出現的確認對話方塊中，選擇 [**確定**] 按鈕。

3. 在 [ **SiteColumnProjectTemplate** ] 節點底下，開啟 SiteColumnProjectTemplate 檔案，然後從其中移除下列元素。

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. 儲存並關閉檔案。

5. 在 [ **SiteColumnProjectTemplate** ] 節點底下，開啟 ProjectTemplate 或 ProjectTemplate 檔案，然後從它移除下列 `PropertyGroup` 元素。

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. 移除下列 `None` 元素。

    ```xml
    <None Include="key.snk" />
    ```

7. 儲存並關閉檔案。

## <a name="associating-the-wizard-with-the-project-template"></a>使 wizard 與專案範本產生關聯
 現在您已完成 wizard，您必須將 wizard 與**Site Column**專案範本產生關聯。 若要執行這項操作，您必須完成三個程式：

1. 以強式名稱簽署 wizard 元件。

2. 取得 wizard 元件的公開金鑰 token。

3. 在 [網站] 資料**行**專案範本的 .vstemplate 檔案中，加入 wizard 元件的參考。

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>使用強式名稱簽署 wizard 元件

1. 在**方案總管**中，開啟**ProjectTemplateWizard**專案的快捷方式功能表，然後選擇 [**屬性**]。

2. 在 [**簽署**] 索引標籤上，選取 [**簽署元件**] 核取方塊。

3. 在 [**選擇強式名稱金鑰**檔] 清單中，選擇 [ **\<新增]。>** 。

4. 在 [**建立強式名稱金鑰**] 對話方塊中，輸入新金鑰檔的名稱，清除 [**以密碼保護我的金鑰**檔] 核取方塊，然後選擇 [**確定]** 按鈕。

5. 開啟**ProjectTemplateWizard**專案的快捷方式功能表，然後選擇 [**建立**] 以建立 ProjectTemplateWizard 檔案。

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>取得 wizard 元件的公開金鑰 token

1. 在 [**開始] 功能表**上，依序選擇 [**所有程式**]、[ **Microsoft Visual Studio**]、[ **Visual Studio Tools**]，然後選擇 [**開發人員命令提示字元**]。

     [Visual Studio 命令提示字元] 視窗隨即開啟。

2. 執行下列命令，將*PathToWizardAssembly*取代為開發電腦上 ProjectTemplateWizard 專案的內建 ProjectTemplateWizard .dll 元件的完整路徑：

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     ProjectTemplateWizard 元件的公開金鑰 token 會寫入 Visual Studio 命令提示字元 視窗中。

3. 將 [Visual Studio 命令提示字元] 視窗保持開啟。 在下一個程式中，您將需要公開金鑰 token。

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>在 .vstemplate 檔案中加入 wizard 元件的參考

1. 在**方案總管**中，展開**SiteColumnProjectTemplate**專案節點，然後開啟 SiteColumnProjectTemplate 檔案。

2. 在檔案結尾附近，于 `</TemplateContent>` 和 `</VSTemplate>` 標記之間新增下列 `WizardExtension` 元素。 以您在上一個程式中取得的公開金鑰 token 取代 `PublicKeyToken` 屬性的*token*值。

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     如需 `WizardExtension` 元素的詳細資訊，請參閱[WizardExtension &#40;元素 Visual Studio&#41;範本](/visualstudio/extensibility/wizardextension-element-visual-studio-templates)。

3. 儲存並關閉檔案。

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>將可取代的參數新增至專案範本中的元素 .xml 檔案
 將數個可取代的參數新增至 SiteColumnProjectTemplate 專案中的*元素 .xml*檔案。 這些參數會在您稍早定義的 `SiteColumnProjectWizard` 類別中的 `RunStarted` 方法中初始化。 當使用者建立網站資料行專案時，Visual Studio 會自動將新專案中的*元素 .xml*檔案中的這些參數取代為在 wizard 中指定的值。

 可取代的參數是以貨幣符號（$）字元開頭和結尾的 token。 除了定義您自己的可取代參數之外，您還可以使用 SharePoint 專案系統所定義和初始化的內建參數。 如需詳細資訊，請參閱可[取代的參數](../sharepoint/replaceable-parameters.md)。

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>若要將可取代的參數新增至元素 .xml 檔案

1. 在 SiteColumnProjectTemplate 專案中，將*元素 .xml*檔案的內容取代為下列 xml。

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

     新的 XML 會將 `Name`、`DisplayName`、`Type`和 `Group` 屬性的值變更為自訂可取代的參數。

2. 儲存並關閉檔案。

## <a name="add-the-wizard-to-the-vsix-package"></a>將嚮導新增至 VSIX 封裝
 若要使用包含網站資料行專案範本的 VSIX 封裝來部署 wizard，請將 wizard 專案和 SharePoint 命令專案的參考加入 VSIX 專案中的 extension.vsixmanifest 檔案。

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>將嚮導加入至 VSIX 封裝

1. 在**方案總管**的**SiteColumnProjectItem**專案中，開啟**extension.vsixmanifest**檔案的快捷方式功能表，然後選擇 [**開啟**]。

     Visual Studio 會在資訊清單編輯器中開啟檔案。

2. 在編輯器的 [**資產**] 索引標籤上，選擇 [**新增**] 按鈕。

     [**加入新資產**] 對話方塊隨即開啟。

3. 在 [**類型**] 清單中，選擇 [ **VisualStudio**]。

4. 在 [**來源**] 清單中，選擇 [**目前方案] 中的專案**。

5. 在 [**專案**] 清單中，選擇 [ **ProjectTemplateWizard**]，然後選擇 [**確定]** 按鈕。

6. 在編輯器的 [**資產**] 索引標籤上，再次選擇 [**新增**] 按鈕。

     [**加入新資產**] 對話方塊隨即開啟。

7. 在 [**類型**] 清單中，輸入 [ **SharePoint**]。

8. 在 [**來源**] 清單中，選擇 [**目前方案] 中的專案**。

9. 在 [**專案**] 清單中，選擇 [ **SharePointCommands** ] 專案，然後選擇 [**確定]** 按鈕。

10. 在功能表列上，選擇 [**組建**] [ > ] [**組建方案**]，然後確定方案的組建不會發生錯誤。

## <a name="test-the-wizard"></a>測試嚮導
 您現在已準備好要測試嚮導。 首先，在 Visual Studio 的實驗實例中，開始對 SiteColumnProjectItem 方案進行調試。 然後，在 Visual Studio 的實驗實例中測試網站資料行專案的 wizard。 最後，建立並執行專案，以確認 [網站] 欄是否如預期般運作。

#### <a name="to-start-debugging-the-solution"></a>開始對方案進行調試

1. 使用系統管理認證重新開機 Visual Studio，然後開啟 SiteColumnProjectItem 解決方案。

2. 在 ProjectTemplateWizard 專案中，開啟 SiteColumnProjectWizard 程式碼檔案，然後將中斷點新增至 `RunStarted` 方法中的第一行程式碼。

3. 在功能表列上，選擇 [ **Debug** > **例外**狀況]。

4. 在 [**例外**狀況] 對話方塊中，確認已清除 [ **Common Language Runtime 例外**狀況的擲回 **] 和 [** **使用者未處理**] 核取方塊，然後選擇 [**確定]** 按鈕。

5. 選擇**F5**鍵或在功能表列上選擇 [ **Debug** ] > [**開始進行調試**程式]，開始進行偵錯工具。

     Visual Studio 會將擴充功能安裝至%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-wizard-in-visual-studio"></a>若要在 Visual Studio 中測試 wizard

1. 在 Visual Studio 的實驗實例中，于功能表列**上選擇 [** 檔案] [檔案] [ > **新增** > **專案**]。

2. 展開 [**視覺C#效果**] 節點或 [ **Visual Basic** ] 節點（視您的專案範本支援的語言而定），展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在專案範本清單中，選擇 [**網站**] [資料行]，將專案命名為**SiteColumnWizardTest**，然後選擇 [**確定]** 按鈕。

4. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早于 `RunStarted` 方法中設定的中斷點上停止。

5. 選擇**F5**鍵，或在功能表列上選擇 [ **debug** ] > [**繼續**]，繼續進行專案的 debug。

6. 在 [ **SharePoint 自訂]** 中，輸入您要用來進行偵錯工具的網站 URL，然後選擇 [**下一步]** 按鈕。

7. 在**SharePoint 自訂嚮導**的第二個頁面中，進行下列選擇：

   - 在 [**類型**] 清單中，選擇 [**布林值**]。

   - 在 [**群組**] 清單中，選擇 [**自訂是/否資料行]** 。

   - 在 [**名稱**] 方塊中，輸入**我的是/否資料行**，然後選擇 [**完成]** 按鈕。

     在**方案總管**中，會出現新的專案，並包含名為**Field1**的專案專案，而 Visual Studio 會在編輯器中開啟專案的*Elements .xml*檔案。

8. 確認*Elements*包含您在嚮導中指定的值。

#### <a name="to-test-the-site-column-in-sharepoint"></a>測試 SharePoint 中的網站資料行

1. 在 Visual Studio 的實驗實例中，選擇**F5**鍵。

     [網站] 欄會封裝並部署到專案所指定的 [**網站 URL** ] 屬性所在的 SharePoint 網站上。 網頁瀏覽器會開啟至此網站的預設頁面。

    > [!NOTE]
    > 如果出現 [**腳本調試已停用**] 對話方塊，請選擇 [**是]** 按鈕以繼續進行專案的 debug。

2. 在 [**網站動作**] 功能表上，選擇 [**網站設定**]。

3. 在 [網站設定] 頁面的 [資源**庫**] 底下，選擇 [**網站資料行**] 連結。

4. 在 [網站] 欄清單中，確認**自訂 [是/否資料行]** 群組包含名為 **[是]/[否] 資料行**的資料行，然後關閉網頁瀏覽器。

## <a name="clean-up-the-development-computer"></a>清理開發電腦
 在您完成專案專案的測試之後，請從 Visual Studio 的實驗實例中移除專案範本。

#### <a name="to-clean-up-the-development-computer"></a>清理開發電腦

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**] > [**擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [**網站資料行**]，然後選擇 [**卸載**] 按鈕。

3. 在出現的對話方塊中，選擇 [是] 按鈕以確認您要卸載擴充功能，然後選擇 [**立即重新開機** **]** 按鈕以完成卸載。

4. 關閉 Visual Studio 的實驗實例，以及開啟 CustomActionProjectItem 方案的實例。

     如需如何部署 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 延伸模組的相關資訊，請參閱[運送 Visual Studio 延伸](/visualstudio/extensibility/shipping-visual-studio-extensions)模組。

## <a name="see-also"></a>請參閱
- [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [為 SharePoint 專案項目建立項目範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 範本結構描述參考](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [如何︰搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
