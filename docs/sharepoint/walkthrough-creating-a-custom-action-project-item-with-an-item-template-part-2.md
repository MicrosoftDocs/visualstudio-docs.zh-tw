---
title: 建立自訂動作專案項目包含項目範本，第 2 部分
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
ms.openlocfilehash: 6fa4915b9621789c68ed994440de3a1ef544c40c
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401172"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>逐步解說：建立自訂動作專案項目與項目範本，第 2 部分
  您定義自訂 SharePoint 專案項目類型，並將它與 Visual Studio 中的項目範本產生關聯之後，您也可以提供範本的精靈。 您可以使用精靈，在使用您的範本將新的執行個體的專案項目加入至專案時，從使用者收集資訊。 您所收集的資訊可以用來初始化專案項目中。

 在本逐步解說中，您會將精靈加入自訂動作專案項目所示[逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。 當使用者將自訂動作專案項目新增至 SharePoint 專案中時，精靈就會收集資訊 （例如其位置和使用者選擇時所要巡覽的 URL） 的自訂動作，並將這項資訊來*Elements.xml*新的專案項目中的檔案。

 本逐步解說將示範下列工作：

- 建立自訂 SharePoint 專案項目類型所關聯的項目範本的精靈。

- 定義自訂的精靈 UI，類似於在 Visual Studio 中的 SharePoint 專案項目的內建的精靈。

- 您可以使用可置換的參數，初始化 SharePoint 專案檔，以您在精靈中所收集的資料。

- 偵錯和測試精靈。

> [!NOTE]
> 您可以下載範例，以從[Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) ，示範如何建立工作流程的自訂活動。

## <a name="prerequisites"></a>必要條件
 若要執行本逐步解說中，您必須先建立 CustomActionProjectItem 解決方案藉由完成[逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。

 您還需要完成這個逐步解說在開發電腦上的下列元件：

- 支援的 Windows、 SharePoint 和 Visual Studio 版本。

- Visual Studio SDK 中。 本逐步解說會使用**VSIX 專案**SDK 來建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識會很有幫助，但並非必要，若要完成本逐步解說：

- Visual Studio 中的專案和項目範本的精靈。 如需詳細資訊，請參閱[如何：使用精靈與專案範本](../extensibility/how-to-use-wizards-with-project-templates.md)而<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面。

- 在 SharePoint 中的自訂動作。 如需詳細資訊，請參閱 <<c0> [ 自訂動作](http://go.microsoft.com/fwlink/?LinkId=177800)。

## <a name="create-the-wizard-project"></a>建立精靈專案
 若要完成此逐步解說中，您必須將專案加入 CustomActionProjectItem 建立方案，您[逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。 您將實作<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面，並在此專案中定義的精靈 UI。

#### <a name="to-create-the-wizard-project"></a>若要建立精靈專案

1. 在 Visual Studio 中，開啟 CustomActionProjectItem 方案

2. 中**方案總管**，開啟方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。

3. 中**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**Windows**節點。

4. 在頂端**新的專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。

5. 選擇**WPF 使用者控制項程式庫**專案範本，請將專案命名**ItemTemplateWizard**，然後選擇**確定** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**ItemTemplateWizard**專案加入方案。

6. 從專案刪除 UserControl1 項目。

## <a name="configure-the-wizard-project"></a>設定精靈專案
 建立精靈之前，您必須新增 Windows Presentation Foundation (WPF) 視窗、 程式碼檔案和專案的組件參考。

#### <a name="to-configure-the-wizard-project"></a>若要設定精靈專案

1. 在 **方案總管**，開啟捷徑功能表，從**ItemTemplateWizard**專案節點，然後選擇**屬性**。

2. 在 **專案設計工具**，請確定目標架構設為.NET Framework 4.5。

     Visual C# 專案，您可以設定此值在**應用程式** 索引標籤。Visual Basic 專案，您可以設定此值在**編譯** 索引標籤。如需詳細資訊，請參閱[如何：以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

3. 在  **ItemTemplateWizard**專案中，加入**視窗 (WPF)** 加入專案中，項目，然後再將項目命名**WizardWindow**。

4. 新增名為 CustomActionWizard 和字串的兩個程式碼檔案。

5. 開啟捷徑功能表**ItemTemplateWizard**專案，，然後選擇**加入參考**。

6. 在 **參考管理員-ItemTemplateWizard**對話方塊的 **組件**節點，選擇 **延伸模組**節點。

7. 選取下列組件中，旁邊的核取方塊，然後選擇**確定**按鈕：

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. 在 **方案總管**，請在**參考**ItemTemplateWizard 專案資料夾，選擇**EnvDTE**參考。

9. 在 [**屬性**] 視窗中，變更的值**內嵌 Interop 類型**屬性設**False**。

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>定義的預設位置和自訂動作的識別碼字串
 每個自訂的動作有位置和中指定的識別碼`GroupID`並`Location`屬性`CustomAction`中的項目*Elements.xml*檔案。 在此步驟中，您會定義一些 ItemTemplateWizard 專案中的這些屬性的有效字串。 當您完成這個逐步解說中時，這些字串會寫入*Elements.xml*自訂動作專案項目時使用者會在精靈中指定 「 位置 」 和 「 識別碼中的檔案。

 為了簡單起見，此範例僅支援部分可用的預設位置和識別碼。 如需完整清單，請參閱 <<c0> [ 預設自訂動作的位置和識別碼](http://go.microsoft.com/fwlink/?LinkId=181964)。

#### <a name="to-define-the-default-location-and-id-strings"></a>若要定義的預設位置和識別碼字串

1. 開啟。

2. 在  **ItemTemplateWizard**專案中，字串的程式碼檔案中的程式碼取代為下列程式碼。

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>建立精靈使用者介面
 新增 XAML 來定義精靈 的 UI，並新增一些程式碼中繫結至控制項的精靈識別碼字串。 您所建立的精靈，類似於 Visual Studio 中的 SharePoint 專案的內建精靈。

#### <a name="to-create-the-wizard-ui"></a>若要建立的精靈 UI

1. 在  **ItemTemplateWizard**專案中，開啟捷徑功能表**WizardWindow.xaml**檔案，然後再選擇 **開啟**設計工具中開啟的視窗。

2. 在 XAML 檢視中，請以下列 XAML 取代目前的 XAML。 XAML 定義 UI，包括標題、 控制的指定行為的自訂動作，並在視窗底部的 瀏覽按鈕。

    > [!NOTE]
    > 您的專案會有某些編譯錯誤之後新增此程式碼。 當您在稍後步驟中加入程式碼時，這些錯誤就會消失運作。

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > 在此 XAML 中建立的視窗衍生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>基底類別。 當您將自訂的 WPF 對話方塊加入 Visual Studio 時，我們建議您將您的對話方塊中衍生自這個類別有一致的樣式，與其他 Visual Studio 中的對話方塊，並避免與強制回應對話方塊時，可能會發生的問題。 如需詳細資訊，請參閱 <<c0> [ 建立和管理強制回應對話方塊](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)。

3. 如果您正在開發 Visual Basic 專案，移除`ItemTemplateWizard`來自命名空間`WizardWindow`中的類別名稱`x:Class`屬性`Window`項目。 此元素會在第一行中的 XAML。 當您完成時，第一行應該類似下列程式碼：

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. 在程式碼後置檔案 WizardWindow.xaml 檔案中，取代下列程式碼中的目前程式碼。

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>實作精靈
 藉由實作定義在精靈的功能<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面。

#### <a name="to-implement-the-wizard"></a>若要實作精靈

1. 在  **ItemTemplateWizard**專案中，開啟**CustomActionWizard**程式碼檔案，並以下列程式碼取代此檔案中目前的程式碼：

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>檢查點
 此時在逐步解說中，精靈的所有程式碼現在是在專案中。 建置專案，以確定它會編譯無誤。

#### <a name="to-build-your-project"></a>建置您的專案

1. 在功能表列上選擇 [建置]   > [建置解決方案]  。

## <a name="associate-the-wizard-with-the-item-template"></a>關聯的項目範本的精靈
 既然您已實作 「 精靈 」，您必須將其與**自訂動作**項目範本，藉由完成三個主要步驟：

1. 精靈組件，以強式名稱簽署。

2. 取得精靈的組件的公開金鑰語彙基元。

3. 在.vstemplate 檔案中新增精靈 的組件的參考**自訂動作**項目範本。

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>若要簽署以強式名稱的組件精靈

1. 在 **方案總管**，開啟捷徑功能表，從**ItemTemplateWizard**專案節點，然後選擇**屬性**。

2. 在  **Signing**索引標籤上，選取**簽署組件**核取方塊。

3. 在 **選擇強式名稱金鑰檔**清單中，選擇 **\<新增...>** 。

4. 中**建立強式名稱金鑰**對話方塊方塊中，輸入名稱，清除**保護我的金鑰檔使用密碼**核取方塊，，然後選擇 [**確定**] 按鈕。

5. 在功能表列上選擇 [建置]   > [建置解決方案]  。

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>若要取得的公開金鑰權杖精靈組件

1. 在 Visual Studio 命令提示字元視窗中，執行下列命令，將*PathToWizardAssembly* ItemTemplateWizard 專案開發上建置的 ItemTemplateWizard.dll 組件的完整路徑電腦。

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     公開金鑰語彙基元*ItemTemplateWizard.dll*組件會寫入至 [Visual Studio 命令提示字元] 視窗。

2. Visual Studio 命令提示字元視窗保持開啟。 您必須完成下一個程序的公開金鑰 token。

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>將.vstemplate 檔案中的精靈組件的參考

1. 在 **方案總管**，展開**ItemTemplate**專案節點，然後再開啟*ItemTemplate.vstemplate*檔案。

2. 接近檔案結尾，新增下列`WizardExtension`之間的項目`</TemplateContent>`和`</VSTemplate>`標記。 取代*YourToken*的值`PublicKeyToken`屬性與您在上一個程序中取得的公開金鑰 token。

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     如需詳細資訊`WizardExtension`項目，請參閱 < [WizardExtension 項目&#40;Visual Studio 範本&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates)。

3. 儲存並關閉檔案。

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>加入可置換的參數，以便*Elements.xml*檔案中的項目範本
 加入數個可取代的參數，以便*Elements.xml* ItemTemplate 專案檔中的。 這些參數會初始化`PopulateReplacementDictionary`方法中的`CustomActionWizard`您稍早定義的類別。 當使用者將自訂動作專案項目加入至專案時，Visual Studio 會自動取代這些參數*Elements.xml*它們在精靈中指定的值與新的專案項目中的檔案。

 可置換的參數是權杖的開始和結束都貨幣符號 （$） 字元。 除了定義您自己可置換的參數，您可以使用內建參數，用於定義 SharePoint 專案系統，並初始化。 如需詳細資訊，請參閱 <<c0> [ 可置換的參數](../sharepoint/replaceable-parameters.md)。

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>若要加入可取代參數*Elements.xml*檔案

1. 在 ItemTemplate 專案中的內容取代*Elements.xml*以下列 XML 檔案。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     新的 XML 變更的值`Id`， `GroupId`， `Location`， `Description`，和`Url`可置換的參數屬性。

2. 儲存並關閉檔案。

## <a name="add-the-wizard-to-the-vsix-package"></a>將精靈加入至 VSIX 封裝
 在 source.extension.vsixmanifest 檔案中在 VSIX 專案，請加入精靈專案的參考，以便部署與 VSIX 封裝，其中包含的專案項目。

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>若要將精靈加入至 VSIX 封裝

1. 在 **方案總管 中**，開啟捷徑功能表，從**source.extension.vsixmanifest** CustomActionProjectItem 專案中的檔案，然後選擇 **開啟**開啟資訊清單編輯器中的檔案。

2. 在資訊清單編輯器中，選擇**資產**索引標籤，然後選擇**新增** 按鈕。

     **加入新資產** 對話方塊隨即出現。

3. 在 **型別**清單中，選擇**Microsoft.VisualStudio.Assembly**。

4. 在 **來源**清單中，選擇**目前方案中的專案**。

5. 在 [**專案**清單中，選擇**ItemTemplateWizard**，然後選擇 **[確定]** ] 按鈕。

6. 在功能表列上選擇 **建置** > **建置方案**，然後確認方案編譯無誤。

## <a name="test-the-wizard"></a>測試精靈
 您現在已準備好測試精靈。 首先，開啟要偵錯 CustomActionProjectItem 方案在 Visual Studio 的實驗執行個體。 接著在 Visual Studio 的實驗執行個體中的 SharePoint 專案中測試自訂動作專案項目精靈。 最後，建置並執行 SharePoint 專案，以確認自訂動作會在如預期般運作。

#### <a name="to-start-to-debug-the-solution"></a>若要開始偵錯方案

1. 使用系統管理認證，重新啟動 Visual Studio，然後開啟 CustomActionProjectItem 解決方案。

2. 在 ItemTemplateWizard 專案中，開啟 CustomActionWizard 程式碼檔案，然後加入中斷點至第一行中的程式碼`RunStarted`方法。

3. 在功能表列上選擇 **偵錯** > **例外狀況**。

4. 在**例外狀況**對話方塊方塊中，請確定**擲回**並**使用者未處理**核取方塊**Common Language Runtime 例外狀況**會先清除，，然後選擇 [ **[確定]** ] 按鈕。

5. 開始偵錯選擇**F5**鍵或，在功能表列選擇**偵錯** > **開始偵錯**。

     Visual Studio 會 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 動作專案 Item\1.0 安裝擴充功能，並啟動 Visual Studio 的實驗執行個體。 在 Visual Studio 這個執行個體中，您將測試專案項目。

#### <a name="to-test-the-wizard-in-visual-studio"></a>若要在 Visual Studio 中測試精靈

1. 在實驗性 Visual Studio 執行個體，在功能表列上，選擇**檔案** > **新增** > **專案**。

2. 依序展開**Visual C#** 或**Visual Basic**節點 （取決於支援的語言項目範本），展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。

3. 在專案範本清單中，選擇**SharePoint 2010 專案**，將專案命名**CustomActionWizardTest**，然後選擇**確定**  按鈕。

4. 在 [ **SharePoint 自訂精靈**，輸入您想要用於偵錯時，網站的 URL，然後選擇**完成**] 按鈕。

5. 在 **方案總管 中**，開啟專案節點的捷徑功能表，選擇**新增**，然後選擇 **新項目**。

6. 在**加入新項目-CustomItemWizardTest**對話方塊方塊中，展開**SharePoint**節點，然後展開**2010年**節點。

7. 在專案項目清單中，選擇**自訂動作**項目，然後再選擇**新增** 按鈕。

8. 確認 Visual Studio 的其他執行個體中的程式碼是在您稍早在設定的中斷點上停止`RunStarted`方法。

9. 繼續偵錯專案，選擇**F5**金鑰或，功能表列選擇**偵錯** > **繼續**。

     SharePoint 自訂精靈 隨即出現。

10. 底下**位置**，選擇 **清單編輯** 選項按鈕。

11. 在 **群組識別碼**清單中，選擇**Communications**。

12. 在 **標題**方塊中，輸入**SharePoint 開發人員中心**。

13. 在 **描述**方塊中，輸入**開啟 SharePoint 開發人員中心網站**。

14. 在 [ **URL**方塊中，輸入 **[https://docs.microsoft.com/sharepoint/dev/](https://docs.microsoft.com/sharepoint/dev/)** ，然後選擇**完成**] 按鈕。

     Visual Studio 會加入名為的項目**CustomAction1**至您的專案，並開啟*Elements.xml*在編輯器中的檔案。 確認*Elements.xml*包含您在精靈中指定的值。

#### <a name="to-test-the-custom-action-in-sharepoint"></a>若要在 SharePoint 中測試自訂動作

1. 在 Visual Studio 的實驗性執行個體，選擇**F5**鍵，或在功能表列上選擇 **偵錯** > **開始偵錯**。

     自訂動作會封裝並部署到 SharePoint 網站所指定**站台 URL**屬性的專案，並在 web 瀏覽器會開啟到這個站台的預設頁面。

    > [!NOTE]
    > 如果**指令碼偵錯已停用** 對話方塊出現時，選擇**是** 按鈕。

2. 在 SharePoint 網站的 [清單] 區域中，選擇**任務**連結。

     **所有工作的工作-** 頁面隨即出現。

3. 上**清單工具**索引標籤的功能區中，選擇**清單** 索引標籤，然後在**設定**群組中，選擇**清單設定**。

     **清單設定**頁面隨即出現。

4. 底下**Communications**靠近頁面頂端的標題之下，選擇**SharePoint 開發人員中心**連結，請確認瀏覽器會開啟網站 https://docs.microsoft.com/sharepoint/dev/，然後關閉瀏覽器。

## <a name="cleaning-up-the-development-computer"></a>清除開發電腦
 完成測試的專案項目之後，請從 Visual Studio 的實驗執行個體中移除專案項目範本。

#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦

1. 在實驗性 Visual Studio 執行個體，在功能表列上，選擇**工具** > **擴充功能和更新**。

     [擴充功能和更新]  對話方塊隨即開啟。

2. 在延伸模組清單中，選擇**自訂動作專案項目**延伸模組，然後選擇**解除安裝** 按鈕。

3. 在出現的對話方塊中，選擇 **[是]** 按鈕，以確認您要解除安裝延伸模組，然後選擇**立即重新啟動**按鈕以完成解除安裝。

4. 關閉 Visual Studio （實驗性執行個體和 CustomActionProjectItem 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。

## <a name="see-also"></a>另請參閱
- [逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 範本結構描述參考](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
- [自訂動作的預設位置和識別碼](http://go.microsoft.com/fwlink/?LinkId=181964)
