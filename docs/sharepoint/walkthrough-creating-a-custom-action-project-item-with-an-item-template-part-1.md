---
title: 使用專案範本建立自訂動作專案專案（第1部分）
titleSuffix: ''
description: 使用專案範本，建立可以加入至 SharePoint 專案的專案專案，以在 SharePoint 網站上建立自訂動作。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 71e9d83cbe3459abb05e24b127e54651aade8ee5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217953"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>逐步解說：使用專案範本建立自訂動作專案專案（第1部分）
  您可以藉由建立自己的專案專案類型，在 Visual Studio 中擴充 SharePoint 專案系統。 在這個逐步解說中，您將建立可加入至 SharePoint 專案的專案專案，以在 SharePoint 網站上建立自訂動作。 自訂動作會將功能表項目加入至 SharePoint 網站的 [ **網站動作** ] 功能表。

 本逐步解說將示範下列工作：

- 建立 Visual Studio 擴充功能，以定義自訂動作的新 SharePoint 專案專案類型。 新的專案專案類型會實作為數個自訂功能：

  - 此快捷方式功能表可作為與專案專案相關之其他工作的起點，例如在 Visual Studio 中顯示自訂動作的設計工具。

  - 當開發人員變更專案專案的特定屬性和包含它的專案時所執行的程式碼。

  - 在 **方案總管** 的專案專案旁出現的自訂圖示。

- 建立專案專案的 Visual Studio 專案範本。

- 建立 Visual Studio 擴充功能 (VSIX) 套件，以部署專案專案範本和延伸模組元件。

- 調試和測試專案專案。

  這是獨立的逐步解說。 完成此逐步解說之後，您可以藉由將嚮導加入至專案範本來增強專案專案。 如需詳細資訊，請參閱 [逐步解說：使用專案範本建立自訂動作專案專案（第2部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。

> [!NOTE]
> 您可以從 [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 下載範例，以示範如何建立工作流程的自訂活動。

## <a name="prerequisites"></a>必要條件
 您需要在開發電腦上執行下列元件，才能完成此逐步解說：

- 支援的 Microsoft Windows、SharePoint 和 Visual Studio 版本。

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說會使用 SDK 中的 **Vsix 專案** 範本來建立 vsix 封裝，以部署專案專案。 如需詳細資訊，請參閱 [Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成此逐步解說：

- SharePoint 中的自訂動作。 如需詳細資訊，請參閱 [自訂動作](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14))。

- Visual Studio 中的專案範本。 如需詳細資訊，請參閱[建立專案和項目範本](../ide/creating-project-and-item-templates.md)。

## <a name="create-the-projects"></a>建立專案
 若要完成這個逐步解說，您必須建立三個專案：

- VSIX 專案。 此專案會建立 VSIX 套件以部署 SharePoint 專案專案。

- 專案範本專案。 這個專案會建立一個專案範本，可用來將 SharePoint 專案專案加入至 SharePoint 專案。

- 類別庫專案。 這個專案會執行定義 SharePoint 專案專案行為的 Visual Studio 延伸模組。

  藉由建立專案來開始逐步解說。

#### <a name="to-create-the-vsix-project"></a>建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

3. 在 [ **新增專案** ] 對話方塊頂端的清單中，確認已選取 [ **.NET Framework 4.5** ]。

4. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [擴充性 **] 節點。**

    > [!NOTE]
    > 只有當您安裝 Visual Studio SDK 時，才能使用擴充 **性節點。** 如需詳細資訊，請參閱本主題稍早的必要條件一節。

5. 選擇 [ **VSIX 專案** ] 範本。

6. 在 [ **名稱** ] 方塊中，輸入 **CustomActionProjectItem**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **CustomActionProjectItem** 專案新增至 **方案總管**。

#### <a name="to-create-the-item-template-project"></a>若要建立專案範本專案

1. 在 **方案總管** 中，開啟方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [ **新增專案** ] 對話方塊頂端的清單中，確認已選取 [ **.NET Framework 4.5** ]。

3. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [擴充性 **] 節點。**

4. 在專案範本清單中，選擇 [ **c # 專案] 範本** 或 **Visual Basic 專案範本** 範本。

5. 在 [ **名稱** ] 方塊中，輸入 **ItemTemplate**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **ItemTemplate** 專案加入至方案。

#### <a name="to-create-the-extension-project"></a>建立延伸模組專案

1. 在 **方案總管** 中，開啟方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [ **新增專案** ] 對話方塊頂端的清單中，確認已選取 [ **.NET Framework 4.5** ]。

3. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** ] 節點，選擇 [ **Windows** ] 節點，然後選擇 [ **類別庫** ] 專案範本。

4. 在 [ **名稱** ] 方塊中，輸入 **ProjectItemDefinition**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **ProjectItemDefinition** 專案加入至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-extension-project"></a>設定擴充功能專案
 在您撰寫程式碼來定義 SharePoint 專案專案類型之前，必須先將程式碼檔和元件參考加入至擴充功能專案。

#### <a name="to-configure-the-project"></a>若要設定專案

1. 在 **方案總管** 中，開啟 **ProjectItemDefinition** 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在專案專案清單中，選擇 [程式 **代碼** 檔案]。

3. 在 [ **名稱** ] 方塊中，輸入具有適當副檔名的名稱 **CustomAction** ，然後選擇 [ **加入** ] 按鈕。

4. 在 **方案總管** 中，開啟 **ProjectItemDefinition** 專案的快捷方式功能表，然後選擇 [ **加入參考**]。

5. 在 [ **參考管理員-ProjectItemDefinition** ] 對話方塊中，選擇 [ **元件** ] 節點，然後選擇 [ **架構** ] 節點。

6. 選取下列每個元件旁的核取方塊：

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. 選擇 [ **擴充** 功能] 節點，選取 [VisualStudio] 元件旁邊的核取方塊，然後選擇 [ **確定]** 按鈕。

## <a name="define-the-new-sharepoint-project-item-type"></a>定義新的 SharePoint 專案專案類型
 建立類別來執行介面， <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 以定義新專案專案類型的行為。 當您想要定義新的專案專案類型時，請執行這個介面。

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>若要定義新的 SharePoint 專案專案類型

1. 在 ProjectItemDefinition 專案中，開啟 CustomAction 程式碼檔案。

2. 以下列程式碼取代此檔案中的程式碼。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb" id="Snippet1":::

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>在方案總管中建立專案專案的圖示
 當您建立自訂 SharePoint 專案專案時，您可以將影像 (圖示或點陣圖) 與專案專案產生關聯。 此影像會出現在 **方案總管** 中專案專案的旁邊。

 在下列程式中，您會建立專案專案的圖示，並將圖示內嵌于擴充元件中。 此圖示是由您稍 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> 早建立之類別的所參考 `CustomActionProjectItemTypeProvider` 。

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>若要建立專案專案的自訂圖示

1. 在 **方案總管** 中，開啟 **ProjectItemDefinition** 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案 ...**]。

2. 在專案專案清單中，選擇 **圖示** 檔專案。

    > [!NOTE]
    > 在 Visual Basic 專案中，您必須選擇 [ **一般** ] 節點來顯示 **圖示** 檔專案。

3. 在 [ **名稱** ] 方塊中，輸入 **CustomAction_SolutionExplorer .ico**，然後選擇 [ **加入** ] 按鈕。

     新的圖示會在 **影像編輯器** 中開啟。

4. 編輯16x16 版本的圖示檔，使其具有可辨識的設計，然後儲存圖示檔。

5. 在 **方案總管** 中，選擇 **CustomAction_SolutionExplorer .ico**。

6. 在 [ **屬性** ] 視窗中，選擇 [ **組建動作** ] 屬性旁邊的箭號。

7. 在出現的清單中，選擇 [ **內嵌資源**]。

## <a name="checkpoint"></a>Checkpoint
 在本逐步解說的這個階段中，專案專案的所有程式碼現在都在專案中。 建立專案以確認它會編譯而不會發生錯誤。

#### <a name="to-build-your-project"></a>建置您的專案

1. 開啟 **ProjectItemDefinition** 專案的快捷方式功能表，然後選擇 [ **建立**]。

## <a name="create-a-visual-studio-item-template"></a>建立 Visual Studio 專案範本
 若要讓其他開發人員能夠使用您的專案專案，您必須建立專案範本或專案範本。 開發人員可以在 Visual Studio 中使用這些範本，藉由建立新的專案或將專案加入至現有的專案，來建立專案專案的實例。 在這個逐步解說中，使用 ItemTemplate 專案來設定您的專案專案。

#### <a name="to-create-the-item-template"></a>建立專案範本

1. 從 ItemTemplate 專案中刪除 Class1 程式碼檔案。

2. 在 ItemTemplate 專案中，開啟 *itemtemplate .vstemplate* 檔案。

3. 以下列 XML 取代檔案的內容，然後儲存並關閉檔案。

    > [!NOTE]
    > 下列 XML 適用于 Visual c # 專案範本。 如果您要建立 Visual Basic 專案範本，請將元素的值取代 `ProjectType` 為 `VisualBasic` 。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     此檔案會定義專案範本的內容和行為。 如需這個檔案內容的詳細資訊，請參閱 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)。

4. 在 **方案總管** 中，開啟 **ItemTemplate** 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

5. 在 [ **加入新專案** ] 對話方塊中，選擇 [ **文字檔** ] 範本。

6. 在 [ **名稱** ] 方塊中，輸入 **CustomAction .spdata**，然後選擇 [ **加入** ] 按鈕。

7. 將下列 XML 新增至 *CustomAction. .spdata* 檔案，然後儲存並關閉檔案。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     此檔案包含專案專案所包含之檔案的相關資訊。 `Type`專案的屬性 `ProjectItem` 必須設定為傳遞至專案專案定義的相同字串， <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> (您稍 `CustomActionProjectItemTypeProvider` 早在本逐步解說中所建立的類別) 。 如需 *.spdata* 檔案內容的詳細資訊，請參閱 [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)。

8. 在 **方案總管** 中，開啟 **ItemTemplate** 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

9. 在 [ **加入新專案** ] 對話方塊中，選擇 [ **XML** 檔案] 範本。

10. 在 [ **名稱** ] 方塊中，輸入 **Elements.xml**，然後選擇 [ **加入** ] 按鈕。

11. 以下列 XML 取代 *Elements.xml* 檔案的內容，然後儲存並關閉檔案。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     此檔案會定義預設的自訂動作，以在 SharePoint 網站的 [ **網站動作** ] 功能表上建立功能表項目。 當使用者選擇功能表項目時，專案中指定的 URL `UrlAction` 會在網頁瀏覽器中開啟。 如需您可以用來定義自訂動作之 XML 元素的詳細資訊，請參閱 [自訂動作定義](/sharepoint/dev/schema/custom-action-definition-schema)。

12. （選擇性）開啟 *ItemTemplate .ico* 檔案並加以修改，使其具有可辨識的設計。 此圖示會顯示在 [ **加入新專案** ] 對話方塊中的專案專案旁。

13. 在 **方案總管** 中，開啟 **ItemTemplate** 專案的快捷方式功能表，然後選擇 **[卸載專案**]。

14. 再次開啟 **ItemTemplate** 專案的快捷方式功能表，然後選擇 [ **編輯 itemtemplate .csproj** ] 或 [ **編輯 itemtemplate. vbproj**]。

15. 在專案檔中找出下列 `VSTemplate` 元素。

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. `VSTemplate`以下列 XML 取代此元素，然後儲存並關閉檔案。

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`元素會在建立專案時，于建立專案範本的路徑中指定其他資料夾。 在這裡指定的資料夾可確保只有當客戶開啟 [ **加入新專案** ] 對話方塊、展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點時，才會提供專案範本。

17. 在 **方案總管** 中，開啟 **ItemTemplate** 專案的快捷方式功能表，然後選擇 [ **重載專案**]。

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>建立 VSIX 套件以部署專案專案
 若要部署擴充功能，請在您的方案中使用 VSIX 專案來建立 VSIX 套件。 首先，藉由修改 VSIX 專案中包含的 extension.vsixmanifest 檔案來設定 VSIX 套件。 然後，建立解決方案來建立 VSIX 套件。

#### <a name="to-configure-and-create-the-vsix-package"></a>設定和建立 VSIX 封裝

1. 在 **方案總管** 中，開啟 CustomActionProjectItem 專案中 **extension.vsixmanifest** 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     Visual Studio 在資訊清單編輯器中開啟檔案。 Extension.vsixmanifest 檔案是所有 VSIX 封裝所需的 extension.vsixmanifest 檔案基礎。 如需此檔案的詳細資訊，請參閱 [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))。

2. 在 [ **產品名稱** ] 方塊中，輸入 **自訂動作專案** 專案。

3. 在 [ **作者** ] 方塊中，輸入 **Contoso**。

4. 在 [ **描述** ] 方塊中，輸入 **代表自訂動作的 SharePoint 專案專案**。

5. 在 [ **資產** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

6. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio**]。

    > [!NOTE]
    > 此值對應至 `ItemTemplate` extension.vsixmanifest 檔案中的元素。 這個元素會識別 VSIX 封裝中包含專案專案範本的子資料夾。 如需詳細資訊，請參閱 [ (VSX 架構) 的 ItemTemplate 元素 ](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))。

7. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

8. 在 [ **專案** ] 清單中，選擇 [ **ItemTemplate**]，然後選擇 [ **確定]** 按鈕。

9. 在 [ **資產** ] 索引標籤中，再次選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

10. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

    > [!NOTE]
    > 此值對應至 `MefComponent` extension.vsixmanifest 檔案中的元素。 這個元素會指定 VSIX 封裝中的擴充元件名稱。 如需詳細資訊，請參閱 [[Microsoft.visualstudio.mefcomponent] 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

11. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

12. 在 [ **專案** ] 清單中，選擇 [ **ProjectItemDefinition**]。

13. 選擇 [確定]  按鈕。

14. 在功能表列上，選擇 [**組建**  >  **組建方案**]，然後確定專案已編譯而不會發生錯誤。

15. 請確定 CustomActionProjectItem 專案的組建輸出檔案夾包含 CustomActionProjectItem .vsix 檔案。

     根據預設，組建輸出檔案夾為。包含 CustomActionProjectItem 專案之資料夾下的 \bin\Debug 資料夾。

## <a name="test-the-project-item"></a>測試專案專案
 您現在已準備好測試專案專案。 首先，在 Visual Studio 的實驗實例中開始對 CustomActionProjectItem 方案進行偵錯工具。 然後，在 Visual Studio 的實驗實例中，測試 SharePoint 專案中的 **自訂動作** 專案專案。 最後，建立並執行 SharePoint 專案，以驗證自訂動作是否如預期般運作。

#### <a name="to-start-debugging-the-solution"></a>開始進行解決方案的調試

1. 使用系統管理認證重新開機 Visual Studio，然後開啟 CustomActionProjectItem 方案。

2. 開啟 CustomAction 程式碼檔案，然後將中斷點新增至方法中的第一行程式碼 `InitializeType` 。

3. 選擇 **F5** 鍵以開始進行調試。

     Visual Studio 將擴充功能安裝至%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom 動作專案 Item\1.0，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-project-item-in-visual-studio"></a>若要在 Visual Studio 中測試專案專案

1. 在 Visual Studio 的實驗實例中 **，選擇功能表** 欄上的 [檔案  >  **新增**  >  **專案**]。

2. 展開 [ **Visual c #** ] 或 [ **Visual Basic** ] (根據專案範本支援的語言) ，展開 [ **SharePoint**]，然後選擇 **2010** 節點。

3. 在專案範本清單中，選擇 [ **SharePoint 2010 專案**]。

4. 在 [ **名稱** ] 方塊中，輸入 **CustomActionTest**，然後選擇 [ **確定]** 按鈕。

5. 在 [ **SharePoint 自訂嚮導]** 中，輸入您要用於偵錯工具的網站 URL，然後選擇 [ **完成]** 按鈕。

6. 在 **方案總管** 中，開啟專案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

7. 在 [**加入新專案**] 對話方塊中，選擇 [ **SharePoint** ] 節點底下的 [ **2010** ] 節點。

     確認 **自訂動作** 專案出現在專案專案清單中。

8. 選擇 [ **自訂動作** ] 專案，然後選擇 [ **新增** ] 按鈕。

     Visual Studio 會將名為 **CustomAction1** 的專案新增至您的專案，並在編輯器中開啟 *Elements.xml* 檔案。

9. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早在此方法中設定的中斷點上停止 `InitializeType` 。

10. 選擇 **F5** 鍵以繼續對專案進行調試。

11. 在 Visual Studio 的實驗實例中，在 **方案總管** 中，開啟 [ **CustomAction1** ] 節點的快捷方式功能表，然後選擇 [ **視圖自訂動作設計** 工具]。

12. 確認訊息框出現，然後選擇 [ **確定]** 按鈕。

     您可以使用這個快捷方式功能表來為開發人員提供其他選項或命令，例如顯示自訂動作的設計工具。

13. 在功能表列上，選擇 [**視圖**  >  **輸出**]。

     [ **輸出** ] 視窗隨即開啟。

14. 在 **方案總管** 中，開啟 **CustomAction1** 專案的快捷方式功能表，然後將其名稱變更為 **MyCustomAction**。

     在 [ **輸出** ] 視窗中，會出現確認訊息。 此訊息是由 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> 您在類別中定義的事件處理常式所撰寫 `CustomActionProjectItemTypeProvider` 。 您可以處理這個事件和其他專案專案事件，以在開發人員修改專案專案時，執行自訂行為。

#### <a name="to-test-the-custom-action-in-sharepoint"></a>若要在 SharePoint 中測試自訂動作

1. 在 Visual Studio 的實驗實例中，開啟 *Elements.xml* 檔案，該檔案是 **MyCustomAction** 專案專案的子系。

2. 在 *Elements.xml* 檔案中，進行下列變更，然後儲存檔案：

    - 在 `CustomAction` 元素中，將 `Id` 屬性設定為 GUID 或某些其他的唯一字串，如下列範例所示：

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - 在 `CustomAction` 元素中，設定 `Title` 屬性，如下列範例所示：

        ```xml
        Title="SharePoint Developer Center"
        ```

    - 在 `CustomAction` 元素中，設定 `Description` 屬性，如下列範例所示：

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - 在 `UrlAction` 元素中，設定 `Url` 屬性，如下列範例所示：

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. 選擇 **F5** 鍵。

     自訂動作會封裝並部署至專案的 [ **網站 URL** ] 屬性中所指定的 SharePoint 網站。 Web 瀏覽器會開啟至此網站的預設頁面。

    > [!NOTE]
    > 如果出現 [ **腳本調試已停用** ] 對話方塊，請選擇 [ **是]** 按鈕以繼續對專案進行調試。

4. 在 [ **網站動作** ] 功能表上，選擇 [ **SharePoint 開發人員中心**]，確認瀏覽器開啟網站 https://docs.microsoft.com/sharepoint/dev/ ，然後關閉 web 瀏覽器。

## <a name="clean-up-the-development-computer"></a>清除開發電腦
 完成專案專案的測試之後，請從 Visual Studio 的實驗實例中移除專案專案範本。

#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**  >  **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [ **自訂動作專案** 專案]，然後選擇 [ **卸載** ] 按鈕。

3. 在出現的對話方塊中，選擇 [ **是** ] 按鈕，確認您想要卸載延伸模組。

4. 選擇 [ **立即重新開機** ] 按鈕以完成卸載。

5. 關閉 Visual Studio 的實驗性實例，以及開啟 CustomActionProjectItem 方案的實例。

## <a name="next-steps"></a>下一步
 完成此逐步解說之後，您可以將嚮導加入至專案範本。 當使用者將自訂動作專案專案加入至 SharePoint 專案時，此 wizard 會收集動作 (的相關資訊，例如其位置和在選擇動作時流覽至的 URL) ，並將這項資訊新增至新專案專案中 *Elements.xml* 的檔案。 如需詳細資訊，請參閱 [逐步解說：使用專案範本建立自訂動作專案專案（第2部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：使用專案範本建立自訂動作專案專案（第2部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [圖示影像編輯器](/cpp/windows/image-editor-for-icons)
- [建立圖示或其他影像 &#40;圖示的影像編輯器&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)