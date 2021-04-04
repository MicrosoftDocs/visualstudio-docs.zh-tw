---
title: 使用專案範本建立網站資料行專案專案（第2部分）
titleSuffix: ''
description: 當使用者使用範本來建立包含專案專案的 SharePoint 專案時，請將嚮導新增至網站資料行專案範本，以收集使用者的資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13a2f2c147bbf175a7601cd465dc8acbba9b5388
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217745"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>逐步解說：使用專案範本建立網站資料行專案專案（第2部分）
  在您定義自訂類型的 SharePoint 專案專案，並將其與 Visual Studio 中的專案範本建立關聯之後，您可能也會想要提供範本的嚮導。 當使用者使用您的範本建立包含專案專案的新專案時，您可以使用此嚮導來收集使用者的資訊。 您收集的資訊可以用來初始化專案專案。

 在這個逐步解說中，您將會在 [ [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)] 所示範的網站資料行專案範本中，加入 wizard。 當使用者建立網站資料行專案時，wizard 會收集網站資料行的相關資訊 (例如其基底類型和群組) ，並將這項資訊新增至新專案中的 *Elements.xml* 檔。

 本逐步解說將示範下列工作：

- 建立與專案範本相關聯之自訂 SharePoint 專案專案類型的 wizard。

- 定義自訂的 wizard UI，類似于 Visual Studio 中 SharePoint 專案的內建功能。

- 建立兩個 *SharePoint 命令* ，以在執行嚮導時用來呼叫本機 SharePoint 網站。 SharePoint 命令是 Visual Studio 擴充功能在 SharePoint 伺服器物件模型中呼叫 Api 時，可使用的方法。 如需詳細資訊，請參閱 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

- 使用可取代的參數，以您在嚮導中收集的資料來初始化 SharePoint 專案檔。

- 在每個新的網站資料行專案實例中建立新的 .snk 檔案。 這個檔案是用來簽署專案輸出，讓 SharePoint 方案元件可以部署到全域組件快取。

- 調試和測試 wizard。

> [!NOTE]
> 如需一系列的範例工作流程，請參閱 [SharePoint workflow 範例](/sharepoint/dev/general-development/sharepoint-workflow-samples)。

## <a name="prerequisites"></a>必要條件
 若要執行這個逐步解說，您必須先完成逐步解說 [：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)來建立 SiteColumnProjectItem 方案。

 您也需要在開發電腦上執行下列元件，才能完成此逐步解說：

- 支援的 Windows、SharePoint 和 Visual Studio 版本。

- Visual Studio SDK。 本逐步解說會使用 SDK 中的 **Vsix 專案** 範本來建立 vsix 封裝，以部署專案專案。 如需詳細資訊，請參閱 [Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成此逐步解說：

- Visual Studio 中專案和專案範本的嚮導。 如需詳細資訊，請參閱 [如何：使用具有專案範本](../extensibility/how-to-use-wizards-with-project-templates.md) 和介面的 [檢查] <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 。

- SharePoint 中的網站資料行。 如需詳細資訊，請參閱資料 [行](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))。

## <a name="understand-the-wizard-components"></a>瞭解 wizard 元件
 本逐步解說中示範的 wizard 包含數個元件。 下表描述這些元件。

|元件|描述|
|---------------|-----------------|
|Wizard 執行|這是名為的類別，它會實 `SiteColumnProjectWizard` 作為 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面。 這個介面會定義當 wizard 開始和完成時，以及在執行嚮導的特定時間，Visual Studio 呼叫的方法。|
|Wizard UI|這是以 WPF 為基礎的視窗，名為 `WizardWindow` 。 此視窗包含兩個名為 `Page1` 和的使用者控制項 `Page2` 。 這些使用者控制項代表 wizard 的兩頁。<br /><br /> 在這個逐步解說中， <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> wizard 執行的方法會顯示 WIZARD UI。|
|Wizard 資料模型|這是名為的中繼類別，可 `SiteColumnWizardModel` 在嚮導 UI 和嚮導的執行之間提供圖層。 這個範例會使用這個類別來協助您抽象化 wizard 的執行和 wizard UI;此類別不是所有嚮導的必要元件。<br /><br /> 在這個逐步解說中，wizard 執行 `SiteColumnWizardModel` 會在顯示嚮導 UI 時，將物件傳遞至嚮導視窗。 Wizard UI 會使用這個物件的方法，在 UI 中儲存控制項的值，並執行工作，例如驗證輸入網站 URL 是否有效。 當使用者完成嚮導之後，嚮導執行會使用 `SiteColumnWizardModel` 物件來判斷 UI 的最終狀態。|
|專案簽署管理員|這是一個名為的 helper 類別，可 `ProjectSigningManager` 供 wizard 的執行用來在每個新的專案實例中建立新的金鑰 .snk 檔案。|
|SharePoint 命令|這些是 wizard 資料模型在執行嚮導時呼叫本機 SharePoint 網站所使用的方法。 由於 SharePoint 命令必須以 .NET Framework 3.5 為目標，因此這些命令會在與其余的 wizard 程式碼不同的元件中執行。|

## <a name="create-the-projects"></a>建立專案
 若要完成這個逐步解說，您必須將數個專案加入至您在逐步解說 [：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)中建立的 SiteColumnProjectItem 方案：

- WPF 專案。 您將會執行 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面，並在此專案中定義嚮導 UI。

- 定義 SharePoint 命令的類別庫專案。 此專案必須以 the.NET Framework 3.5 為目標。

  藉由建立專案來開始逐步解說。

#### <a name="to-create-the-wpf-project"></a>若要建立 WPF 專案

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，開啟 SiteColumnProjectItem 方案。

2. 在 **方案總管** 中，開啟 [ **SiteColumnProjectItem** ] 方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

3. 在 [ **加入新專案** ] 對話方塊頂端，確定已在 .NET Framework 版本清單中選擇 **.NET Framework 4.5** 。

4. 展開 [ **Visual c #** ] 節點或 **Visual Basic** 節點，然後選擇 [ **Windows** ] 節點。

5. 在專案範本清單中，選擇 [ **WPF 使用者控制項程式庫**]，將專案命名為 **ProjectTemplateWizard**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **ProjectTemplateWizard** 專案加入至方案，並開啟預設 UserControl1 .xaml 檔案。

6. 從專案中刪除 UserControl1 .xaml 檔案。

#### <a name="to-create-the-sharepoint-commands-project"></a>若要建立 SharePoint 命令專案

1. 在 **方案總管** 中，開啟 [SiteColumnProjectItem] 方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [ **加入新專案** ] 對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 3.5** 。

3. 展開 [ **Visual c #** ] 節點或  **Visual Basic** 節點，然後選擇 [ **Windows** ] 節點。

4. 選擇 [ **類別庫** ] 專案範本、將專案命名為 **SharePointCommands**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **SharePointCommands** 專案加入至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-projects"></a>設定專案
 建立嚮導之前，您必須將一些程式碼檔案和元件參考加入至專案。

#### <a name="to-configure-the-wizard-project"></a>若要設定 wizard 專案

1. 在 **方案總管** 中，開啟 [ **ProjectTemplateWizard** ] 專案節點的快捷方式功能表，然後選擇 [ **屬性**]。

2. 在 [ **專案設計** 工具] 中，選擇 Visual c # 專案的 [ **應用程式** ] 索引標籤或 Visual Basic 專案的 [ **編譯** ] 索引標籤。

3. 請確定目標 framework 設定為 .NET Framework 4.5，而不是 .NET Framework 4.5 用戶端設定檔。

     如需詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../ide/visual-studio-multi-targeting-overview.md)。

4. 開啟 **ProjectTemplateWizard** 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

5. 選擇 **視窗 (WPF)** 專案、將專案命名為 **WizardWindow**，然後選擇 [ **加入** ] 按鈕。

6. 將 **(WPF)** 專案的兩個使用者控制項新增至專案，並將其命名為 **Page1** 和 **Page2**。

7. 將四個程式碼檔案新增至專案，並為其指定下列名稱：

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. 開啟 **ProjectTemplateWizard** 專案節點的快捷方式功能表，然後選擇 [ **加入參考**]。

9. 展開 [ **元件** ] 節點，選擇 [ **擴充** 功能] 節點，然後選取下列元件旁邊的核取方塊：

    - EnvDTE

    - VisualStudio： Interop

    - VisualStudio SharePoint

    - VisualStudio. 11。0

    - VisualStudio <..。

    - VisualStudio <. a. 11。0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. 選擇 [ **確定]** 按鈕，將元件新增至專案。

11. 在 **方案總管** 的 [ **ProjectTemplateWizard** ] 專案的 [**參考**] 資料夾下，選擇 [ **EnvDTE**]。

12. 在 [ **屬性** ] 視窗中，將 [ **內嵌 Interop 類型** ] 屬性的值變更為 [ **False**]。

13. 如果您要開發 Visual Basic 專案，請使用 [ **專案設計** 工具] 將 ProjectTemplateWizard 命名空間匯入至專案。

     如需詳細資訊，請參閱 [如何：新增或移除匯入的命名空間 &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)。

#### <a name="to-configure-the-sharepointcommands-project"></a>設定 SharePointcommands 專案

1. 在 **方案總管** 中，選擇 [ **SharePointCommands** ] 專案節點。

2. 在功能表列上，選擇 [ **專案**]、[  **加入現有專案**]。

3. 在 [ **加入現有專案** ] 對話方塊中，流覽至包含 ProjectTemplateWizard 專案程式碼檔的資料夾，然後選擇 **CommandIds** 程式碼檔案。

4. 選擇 [ **加入** ] 按鈕旁的箭號，然後在出現的功能表上選擇 [ **加入為] 連結** 選項。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將程式碼檔案加入至 **SharePointCommands** 專案做為連結。 程式碼檔案位於 **ProjectTemplateWizard** 專案中，但檔案中的程式碼也會在 **SharePointCommands** 專案中編譯。

5. 在 **SharePointCommands** 專案中，加入另一個名為命令的程式碼檔案。

6. 選擇 [SharePointCommands] 專案，然後在功能表列上選擇 [**專案**  >  **加入參考**]。

7. 展開 [ **元件** ] 節點，選擇 [ **擴充** 功能] 節點，然後選取下列元件旁邊的核取方塊：

    - Microsoft SharePoint

    - VisualStudio 命令

8. 選擇 [ **確定]** 按鈕，將元件新增至專案。

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>建立嚮導模型、簽署管理員和 SharePoint 命令識別碼
 將程式碼加入至 ProjectTemplateWizard 專案，以在範例中執行下列元件：

- SharePoint 命令識別碼。 這些字串會識別 wizard 使用的 SharePoint 命令。 稍後在此逐步解說中，您會將程式碼加入至 SharePointCommands 專案，以執行命令。

- Wizard 資料模型。

- 專案簽署管理員。

  如需這些元件的詳細資訊，請參閱 [瞭解 wizard 元件](#understand-the-wizard-components)。

#### <a name="to-define-the-sharepoint-command-ids"></a>若要定義 SharePoint 命令識別碼

1. 在 ProjectTemplateWizard 專案中，開啟 CommandIds 程式碼檔案，然後將此檔案的整個內容取代為下列程式碼。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb" id="Snippet5":::

#### <a name="to-create-the-wizard-model"></a>建立嚮導模型

1. 開啟 SiteColumnWizardModel 程式碼檔案，並將此檔案的整個內容取代為下列程式碼。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs" id="Snippet6":::

#### <a name="to-create-the-project-signing-manager"></a>若要建立專案簽署管理員

1. 開啟 ProjectSigningManager 程式碼檔案，然後將此檔案的整個內容取代為下列程式碼。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb" id="Snippet8":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs" id="Snippet8":::

## <a name="create-the-wizard-ui"></a>建立嚮導 UI
 加入 XAML 來定義嚮導視窗的 UI，以及兩個提供 wizard 頁面 UI 的使用者控制項，並加入程式碼來定義視窗和使用者控制項的行為。 您建立的 wizard 類似于 Visual Studio 中的 SharePoint 專案的內建 wizard。

> [!NOTE]
> 在下列步驟中，當您將 XAML 或程式碼加入至專案之後，您的專案將會有一些編譯錯誤。 當您在後續步驟中新增程式碼時，這些錯誤就會消失。

#### <a name="to-create-the-wizard-window-ui"></a>建立嚮導視窗 UI

1. 在 ProjectTemplateWizard 專案中，開啟 WizardWindow .xaml 檔案的快捷方式功能表，然後選擇 [ **開啟** ]，在設計工具中開啟視窗。

2. 在設計工具的 XAML 視圖中，以下列 XAML 取代目前的 XAML。 XAML 定義的 UI 包含標題、 <xref:System.Windows.Controls.Grid> 包含 wizard 頁面的，以及視窗底部的導覽按鈕。

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml" id="Snippet10":::

    > [!NOTE]
    > 在此 XAML 中建立的視窗衍生自 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 基類。 當您加入自訂 WPF 對話方塊來 Visual Studio 時，建議您從此類別衍生您的對話方塊，使其符合其他 Visual Studio 對話方塊的樣式，並避免可能發生的強制回應對話方塊問題。 如需詳細資訊，請參閱 [建立和管理模式對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md)。

3. 如果您正在開發 Visual Basic 專案，請從專案的 `ProjectTemplateWizard` `WizardWindow` 屬性中的類別名稱移除命名空間 `x:Class` `Window` 。 此元素位於 XAML 的第一行。 當您完成時，第一行看起來應該如下列範例所示。

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. 開啟 WizardWindow .xaml 檔案的程式碼後端檔案。

5. 以下列程式碼取代此檔案的內容，但位於檔案頂端的宣告除外 `using` 。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs" id="Snippet4":::

#### <a name="to-create-the-first-wizard-page-ui"></a>建立第一個嚮導頁面 UI

1. 在 ProjectTemplateWizard 專案中，開啟 Page1 檔案的快捷方式功能表，然後選擇 [ **開啟** ]，在設計工具中開啟使用者控制項。

2. 在設計工具的 XAML 視圖中，以下列 XAML 取代目前的 XAML。 XAML 會定義包含文字方塊的 UI，讓使用者可以在其中輸入要用於偵錯工具之本機網站的 URL。 UI 也包含選項按鈕，讓使用者可以指定是否要沙箱化專案。

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml" id="Snippet11":::

3. 如果您正在開發 Visual Basic 專案，請從專案的 `ProjectTemplateWizard` `Page1` 屬性中的類別名稱移除命名空間 `x:Class` `UserControl` 。 這是在 XAML 的第一行。 當您完成時，第一行應該如下所示。

    ```xml
    <UserControl x:Class="Page1"
    ```

4. `using`以下列程式碼取代位於檔案最上方的宣告以外的 Page1 檔案內容。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs" id="Snippet2":::

#### <a name="to-create-the-second-wizard-page-ui"></a>若要建立第二個 wizard 頁面 UI

1. 在 ProjectTemplateWizard 專案中，開啟 Page2 .xaml 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     使用者控制項隨即在設計工具中開啟。

2. 在 XAML 視圖中，以下列 XAML 取代目前的 XAML。 XAML 會定義 UI，其中包含一個下拉式清單，可供您選擇網站資料行的基底類型、用於指定內建或自訂群組的下拉式方塊，以顯示資源庫中的網站資料行，以及用來指定網站資料行名稱的文字方塊。

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml" id="Snippet12":::

3. 如果您正在開發 Visual Basic 專案，請從專案的 `ProjectTemplateWizard` `Page2` 屬性中的類別名稱移除命名空間 `x:Class` `UserControl` 。 這是在 XAML 的第一行。 當您完成時，第一行應該如下所示。

    ```xml
    <UserControl x:Class="Page2"
    ```

4. 以下列程式碼取代 Page2 檔案的程式碼後端檔案內容（位於檔案頂端的宣告除外） `using` 。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs" id="Snippet3":::

## <a name="implement-the-wizard"></a>執行嚮導
 藉由執行介面來定義嚮導的主要功能 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 。 這個介面會定義當 wizard 開始和完成時，以及在執行嚮導的特定時間，Visual Studio 呼叫的方法。

#### <a name="to-implement-the-wizard"></a>若要執行嚮導

1. 在 ProjectTemplateWizard 專案中，開啟 SiteColumnProjectWizard 程式碼檔案。

2. 將此檔案的整個內容取代為下列程式碼。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs" id="Snippet7":::

## <a name="create-the-sharepoint-commands"></a>建立 SharePoint 命令
 建立兩個呼叫 SharePoint 伺服器物件模型的自訂命令。 其中一個命令會決定使用者在 wizard 中輸入的網站 URL 是否有效。 另一個命令會從指定的 SharePoint 網站取得所有欄位類型，讓使用者可以選取要使用哪一個做為新網站資料行的基礎。

#### <a name="to-define-the-sharepoint-commands"></a>若要定義 SharePoint 命令

1. 在 **SharePointCommands** 專案中，開啟命令程式碼檔。

2. 將此檔案的整個內容取代為下列程式碼。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb" id="Snippet9":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs" id="Snippet9":::

## <a name="checkpoint"></a>Checkpoint
 在本逐步解說的這個階段中，wizard 的所有程式碼現在都在專案中。 建立專案，以確定它會進行編譯而不會發生錯誤。

#### <a name="to-build-your-project"></a>建置您的專案

1. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

## <a name="removing-the-keysnk-file-from-the-project-template"></a>從專案範本中移除金鑰 .snk 檔案
 在 [逐步解說：使用專案範本建立網站資料行專案專案（第1部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)）中，您建立的專案範本包含用來簽署每個網站資料行專案實例的金鑰 .snk 檔案。 因為嚮導現在會為每個專案產生新的金鑰 .snk 檔案，所以不再需要此金鑰 .snk 檔案。 從專案範本中移除金鑰 .snk 檔案，並移除對此檔案的參考。

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>從專案範本中移除金鑰 .snk 檔案

1. 在 **方案總管** 的 [ **SiteColumnProjectTemplate** ] 節點底下，開啟機 **碼 .snk** 檔案的快捷方式功能表，然後選擇 [ **刪除**]。

2. 在隨後出現的確認對話方塊中選擇 [**確定**] 按鈕。

3. 在 [ **SiteColumnProjectTemplate** ] 節點底下，開啟 SiteColumnProjectTemplate .vstemplate 檔案，然後從中移除下列元素。

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. 儲存並關閉檔案。

5. 在 [ **SiteColumnProjectTemplate** ] 節點底下，開啟 ProjectTemplate .Csproj 或 ProjectTemplate. vbproj 檔案，然後從中移除下列 `PropertyGroup` 元素。

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

## <a name="associating-the-wizard-with-the-project-template"></a>建立 wizard 與專案範本的關聯
 現在您已完成嚮導，您必須將 wizard 與 **網站資料行** 專案範本建立關聯。 若要這樣做，您必須完成三個程式：

1. 使用強式名稱簽署嚮導元件。

2. 取得 wizard 元件的公開金鑰 token。

3. 在 [網站] 資料 **行** 專案範本的 .vstemplate 檔案中，加入 wizard 元件的參考。

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>使用強式名稱簽署 wizard 元件

1. 在 **方案總管** 中，開啟 **ProjectTemplateWizard** 專案的快捷方式功能表，然後選擇 [ **屬性**]。

2. 在 [簽署] 索引標籤上，選取 [簽署組件] 核取方塊。

3. 在 [ **選擇強式名稱金鑰** 檔] 清單中，選擇 [] **\<New...>** 。

4. 在 [ **建立強式名稱金鑰** ] 對話方塊中，輸入新金鑰檔的名稱，清除 [ **以密碼保護我的金鑰** 檔案] 核取方塊，然後選擇 [ **確定]** 按鈕。

5. 開啟 **ProjectTemplateWizard** 專案的快捷方式功能表，然後選擇 [ **建立** ] 以建立 ProjectTemplateWizard.dll 檔案。

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>取得 wizard 元件的公開金鑰 token

1. 在 [ **開始] 功能表** 上，依序選擇 [ **所有程式**]、[ **Microsoft Visual Studio**]、[ **Visual Studio Tools**]，然後選擇 [ **開發人員命令提示字元**]。

     Visual Studio 的命令提示字元視窗隨即開啟。

2. 執行下列命令，將 *PathToWizardAssembly* 取代為您開發電腦上 ProjectTemplateWizard 專案之內建 ProjectTemplateWizard.dll 元件的完整路徑：

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     ProjectTemplateWizard.dll 元件的公開金鑰 token 會寫入 Visual Studio 命令提示字元視窗。

3. 讓 Visual Studio 的命令提示字元視窗保持開啟。 在下一個程式中，您將需要公開金鑰 token。

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>在 .vstemplate 檔案中加入 wizard 元件的參考

1. 在 **方案總管** 中，展開 [ **SiteColumnProjectTemplate** ] 專案節點，然後開啟 SiteColumnProjectTemplate .vstemplate 檔案。

2. 在檔案結尾附近， `WizardExtension` 于和標記之間新增下列元素 `</TemplateContent>` `</VSTemplate>` 。  `PublicKeyToken` 以您在上一個程式中取得的公開金鑰 token 取代屬性的 token 值。

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     如需專案的詳細資訊 `WizardExtension` ，請參閱 [&#40;Visual Studio 範本&#41;的 WizardExtension 元素 ](../extensibility/wizardextension-element-visual-studio-templates.md)。

3. 儲存並關閉檔案。

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>在專案範本的 Elements.xml 檔案中新增可替換的參數
 在 SiteColumnProjectTemplate 專案的 *Elements.xml* 檔案中新增數個可取代的參數。 這些參數會在您稍 `RunStarted` 早定義之類別的方法中初始化 `SiteColumnProjectWizard` 。 當使用者建立網站資料行專案時，Visual Studio 會自動將新專案中 *Elements.xml* 檔案中的這些參數取代為在 [wizard] 中指定的值。

 可取代的參數是以貨幣符號 ($) 字元開頭和結尾的權杖。 除了定義您自己的可取代參數之外，您還可以使用由 SharePoint 專案系統定義和初始化的內建參數。 如需詳細資訊，請參閱可 [取代的參數](../sharepoint/replaceable-parameters.md)。

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>將可取代的參數新增至 Elements.xml 檔案

1. 在 SiteColumnProjectTemplate 專案中，使用下列 XML 來取代 *Elements.xml* 檔案的內容。

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

     新的 XML 會將 `Name` 、 `DisplayName` 、和屬性的值變更 `Type` `Group` 為自訂可取代的參數。

2. 儲存並關閉檔案。

## <a name="add-the-wizard-to-the-vsix-package"></a>將嚮導新增至 VSIX 套件
 若要使用包含網站資料行專案範本的 VSIX 套件來部署嚮導，請將 wizard 專案和 SharePoint 命令專案的參考加入至 VSIX 專案中的 extension.vsixmanifest 檔案。

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>將嚮導加入 VSIX 套件

1. 在 [ **方案總管**] 的 [ **SiteColumnProjectItem** ] 專案中，開啟 **extension.vsixmanifest** 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     Visual Studio 在資訊清單編輯器中開啟檔案。

2. 在編輯器的 [ **資產** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即開啟。

3. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio**]。

4. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

5. 在 [ **專案** ] 清單中，選擇 [ **ProjectTemplateWizard**]，然後選擇 [ **確定]** 按鈕。

6. 在編輯器的 [ **資產** ] 索引標籤上，再次選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即開啟。

7. 在 [ **類型** ] 清單中，輸入 [ **SharePoint**]。

8. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

9. 在 [ **專案** ] 清單中，選擇 [ **SharePointCommands** ] 專案，然後選擇 [ **確定]** 按鈕。

10. 在功能表列上，選擇 [**組建**  >  **組建方案**]，然後確定方案建立時沒有錯誤。

## <a name="test-the-wizard"></a>測試嚮導
 您現在已準備好測試 wizard。 首先，在 Visual Studio 的實驗實例中開始對 SiteColumnProjectItem 方案進行偵錯工具。 然後，在 Visual Studio 的實驗實例中測試網站資料行專案的 wizard。 最後，建立並執行專案，以確認 site 資料行如預期般運作。

#### <a name="to-start-debugging-the-solution"></a>開始進行解決方案的調試

1. 使用系統管理認證重新開機 Visual Studio，然後開啟 SiteColumnProjectItem 方案。

2. 在 ProjectTemplateWizard 專案中，開啟 SiteColumnProjectWizard 程式碼檔案，然後將中斷點加入至方法中的第一行程式碼 `RunStarted` 。

3. 在功能表列上，選擇 [ **Debug**  >  **例外** 狀況]。

4. 在 [**例外** 狀況] 對話方塊中，確定已清除 [ **Common Language Runtime 例外** 狀況] 的 [擲回 **] 和 [** **使用者未處理**] 核取方塊，然後選擇 [**確定]** 按鈕。

5. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **開始調試** 程式]，以開始進行偵錯工具。

     Visual Studio 將擴充功能安裝到%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-wizard-in-visual-studio"></a>若要在 Visual Studio 中測試嚮導

1. 在 Visual Studio 的實驗實例中 **，選擇功能表** 欄上的 [檔案  >  **新增**  >  **專案**]。

2. 展開 [ **Visual c #** ] 節點或 [ **Visual Basic** 節點 (依據您的專案範本所支援的語言) ，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在專案範本清單中，選擇 [ **網站資料行**]、將專案命名為 **SiteColumnWizardTest**，然後選擇 [ **確定]** 按鈕。

4. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早在此方法中設定的中斷點上停止 `RunStarted` 。

5. 選擇 **F5** 鍵或在功能表列上選擇 [ **debug** continue]，繼續進行專案的偵錯工具  >  ****。

6. 在 [ **SharePoint 自訂嚮導]** 中，輸入您要用於偵錯工具的網站 URL，然後選擇 [ **下一步]** 按鈕。

7. 在 [ **SharePoint 自訂] 嚮導** 的第二個頁面中，進行下列選擇：

   - 在 [ **類型** ] 清單中，選擇 [ **布林值**]。

   - 在 [ **群組** ] 清單中，選擇 [ **自訂是/否資料行]**。

   - 在 [ **名稱** ] 方塊中，輸入 [ **是]/[否**] 資料行，然後選擇 [ **完成]** 按鈕。

     在 **方案總管** 中，新專案隨即出現，並包含名為 **Field1** 的專案專案，Visual Studio 在編輯器中開啟專案的 *Elements.xml* 檔。

8. 確認 *Elements.xml* 包含您在嚮導中指定的值。

#### <a name="to-test-the-site-column-in-sharepoint"></a>測試 SharePoint 中的網站資料行

1. 在 Visual Studio 的實驗實例中，選擇 **F5** 鍵。

     網站資料行會封裝並部署到 SharePoint 網站，而專案的 [ **網站 URL** ] 屬性會指定此資料行。 Web 瀏覽器會開啟至此網站的預設頁面。

    > [!NOTE]
    > 如果出現 [ **腳本調試已停用** ] 對話方塊，請選擇 [ **是]** 按鈕以繼續對專案進行調試。

2. 在 [ **網站動作** ] 功能表上，選擇 [ **網站設定**]。

3. 在 [網站設定] 頁面的 [資源 **庫**] 下，選擇 [ **網站資料行** ] 連結。

4. 在 [網站資料行] 清單中，確認 **自訂 [是]/[否]** 資料行群組是否包含名為 **[是]/[否] 資料行** 的資料行，然後關閉 web 瀏覽器。

## <a name="clean-up-the-development-computer"></a>清除開發電腦
 完成專案專案的測試之後，請從 Visual Studio 的實驗實例中移除專案範本。

#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**  >  **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [ **網站資料行**]，然後選擇 [ **卸載** ] 按鈕。

3. 在出現的對話方塊中，選擇 [是] 按鈕，確認您要卸載擴充功能，然後選擇 [**立即重新開機** **]** 按鈕以完成卸載。

4. 關閉 Visual Studio 的實驗性實例，以及開啟 CustomActionProjectItem 方案的實例。

     如需如何部署擴充功能的詳細資訊 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，請參閱 [寄送 Visual Studio 延伸](../extensibility/shipping-visual-studio-extensions.md)模組。

## <a name="see-also"></a>另請參閱
- [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [為 SharePoint 專案項目建立項目範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
