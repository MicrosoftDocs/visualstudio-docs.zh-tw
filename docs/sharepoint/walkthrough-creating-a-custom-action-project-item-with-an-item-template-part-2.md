---
title: 使用專案範本建立自訂動作專案專案（第2部分）
titleSuffix: ''
description: 在這個逐步解說中，當使用者使用專案範本在 SharePoint 網站上加入自訂動作專案專案時，請加入嚮導來收集使用者的資訊。
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
ms.openlocfilehash: 4b6fad27342c086e551320977cdf712f816b383c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217940"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>逐步解說：使用專案範本建立自訂動作專案專案（第2部分）
  在您定義自訂類型的 SharePoint 專案專案，並將其與 Visual Studio 中的專案範本建立關聯之後，您可能也會想要提供範本的嚮導。 當使用者使用您的範本將新的專案專案實例加入至專案時，您可以使用此嚮導來收集使用者的資訊。 您收集的資訊可以用來初始化專案專案。

 在這個逐步解說中，您將會在 [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)中所示範的自訂動作專案專案中，加入 wizard。 當使用者將自訂動作專案專案加入至 SharePoint 專案時，此 wizard 會收集自訂 (動作的相關資訊，例如其位置和流覽至使用者選擇) 的 URL，並將這項資訊新增至新專案專案中 *Elements.xml* 的檔案。

 本逐步解說將示範下列工作：

- 建立與專案範本相關聯之自訂 SharePoint 專案專案類型的 wizard。

- 定義自訂的 wizard UI，類似于 Visual Studio 中的 SharePoint 專案專案內建的 wizard。

- 使用可取代的參數，以您在嚮導中收集的資料來初始化 SharePoint 專案檔。

- 調試和測試 wizard。

> [!NOTE]
> 您可以從 [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 下載範例，以示範如何建立工作流程的自訂活動。

## <a name="prerequisites"></a>必要條件
 若要執行這個逐步解說，您必須先完成逐步解說 [：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)來建立 CustomActionProjectItem 方案。

 您也需要在開發電腦上執行下列元件，才能完成此逐步解說：

- 支援的 Windows、SharePoint 和 Visual Studio 版本。

- Visual Studio SDK。 本逐步解說會使用 SDK 中的 **Vsix 專案** 範本來建立 vsix 封裝，以部署專案專案。 如需詳細資訊，請參閱 [Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成此逐步解說：

- Visual Studio 中專案和專案範本的嚮導。 如需詳細資訊，請參閱 [如何：使用具有專案範本](../extensibility/how-to-use-wizards-with-project-templates.md) 和介面的 [檢查] <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 。

- SharePoint 中的自訂動作。 如需詳細資訊，請參閱 [自訂動作](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14))。

## <a name="create-the-wizard-project"></a>建立 wizard 專案
 若要完成這個逐步解說，您必須將專案加入至您在 [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)中所建立的 CustomActionProjectItem 方案。 您將會執行 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面，並在此專案中定義嚮導 UI。

#### <a name="to-create-the-wizard-project"></a>建立 wizard 專案

1. 在 Visual Studio 中，開啟 CustomActionProjectItem 方案

2. 在 **方案總管** 中，開啟方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

3. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [ **Windows** ] 節點。

4. 在 [ **新增專案** ] 對話方塊頂端，確定已在 .NET Framework 的版本清單中選擇 **.NET Framework 4.5** 。

5. 選擇 [ **WPF 使用者控制項程式庫** ] 專案範本、將專案命名為 **ItemTemplateWizard**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **ItemTemplateWizard** 專案加入至方案。

6. 從專案中刪除 UserControl1 專案。

## <a name="configure-the-wizard-project"></a>設定 wizard 專案
 建立嚮導之前，您必須將 Windows Presentation Foundation (WPF) 視窗、程式碼檔案，以及專案的元件參考。

#### <a name="to-configure-the-wizard-project"></a>若要設定 wizard 專案

1. 在 **方案總管** 中，開啟 **ItemTemplateWizard** 專案節點的快捷方式功能表，然後選擇 [ **屬性**]。

2. 在 [ **專案設計** 工具] 中，確認 [目標 framework] 設定為 .NET Framework 4.5。

     針對 Visual c # 專案，您可以在 [ **應用程式** ] 索引標籤上設定這個值。針對 Visual Basic 的專案，您可以在 [ **編譯** ] 索引標籤上設定這個值。如需詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../ide/visual-studio-multi-targeting-overview.md)。

3. 在 **ItemTemplateWizard** 專案中，將 **視窗 (WPF)** 專案加入至專案，然後將專案命名為 **WizardWindow**。

4. 加入兩個名為 CustomActionWizard 和字串的程式碼檔案。

5. 開啟 **ItemTemplateWizard** 專案的快捷方式功能表，然後選擇 [ **加入參考**]。

6. 在 [ **參考管理員-ItemTemplateWizard** ] 對話方塊的 [ **元件** ] 節點下，選擇 [ **擴充** 功能] 節點。

7. 選取下列元件旁邊的核取方塊，然後選擇 [ **確定]** 按鈕：

    - EnvDTE

    - VisualStudio. 11。0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. 在 [ **方案總管**] 的 [ItemTemplateWizard] 專案的 [ **參考** ] 資料夾中，選擇 **EnvDTE** 參考。

9. 在 [ **屬性** ] 視窗中，將 [ **內嵌 Interop 類型** ] 屬性的值變更為 [ **False**]。

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>定義自訂動作的預設位置和識別碼字串
 每個自訂動作都具有在Elements.xml檔案中專案的和屬性中指定的位置和識別碼 `GroupID` `Location` `CustomAction` 。  在此步驟中，您會在 ItemTemplateWizard 專案中定義這些屬性的部分有效字串。 當您完成此逐步解說時，當使用者在嚮導中指定位置和識別碼時，這些字串會寫入自訂動作專案專案中的 *Elements.xml* 檔案。

 為了簡單起見，此範例僅支援可用預設位置和識別碼的子集。 如需完整清單，請參閱 [預設自訂動作位置和識別碼](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))。

#### <a name="to-define-the-default-location-and-id-strings"></a>若要定義預設位置和識別碼字串

1. 打開。

2. 在 **ItemTemplateWizard** 專案中，以下列程式碼取代字串程式碼檔中的程式碼。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb" id="Snippet6":::

## <a name="create-the-wizard-ui"></a>建立嚮導 UI
 加入 XAML 來定義嚮導的 UI，並加入一些程式碼，將 wizard 中的一些控制項系結至識別碼字串。 您建立的 wizard 類似于 Visual Studio 中的 SharePoint 專案的內建 wizard。

#### <a name="to-create-the-wizard-ui"></a>建立嚮導 UI

1. 在 **ItemTemplateWizard** 專案中，開啟 **WizardWindow .xaml** 檔案的快捷方式功能表，然後選擇 [ **開啟** ]，在設計工具中開啟視窗。

2. 在 XAML 視圖中，以下列 XAML 取代目前的 XAML。 XAML 定義的 UI 包含標題、指定自訂動作行為的控制項，以及視窗底部的導覽按鈕。

    > [!NOTE]
    > 新增此程式碼之後，您的專案將會有一些編譯錯誤。 當您在後續步驟中新增程式碼時，這些錯誤就會消失。

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml" id="Snippet9":::

    > [!NOTE]
    > 在此 XAML 中建立的視窗衍生自 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 基類。 當您加入自訂 WPF 對話方塊來 Visual Studio 時，建議您從此類別衍生您的對話方塊，使其符合 Visual Studio 中其他對話方塊的樣式，並避免強制回應對話方塊可能發生的問題。 如需詳細資訊，請參閱 [建立和管理模式對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md)。

3. 如果您正在開發 Visual Basic 專案，請從專案的 `ItemTemplateWizard` `WizardWindow` 屬性中的類別名稱移除命名空間 `x:Class` `Window` 。 此元素位於 XAML 的第一行。 當您完成時，第一行應該會與下列程式碼類似：

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. 在 WizardWindow .xaml 檔案的程式碼後端檔案中，以下列程式碼取代目前的程式碼。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs" id="Snippet7":::

## <a name="implement-the-wizard"></a>執行嚮導
 藉由執行介面來定義嚮導的功能 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 。

#### <a name="to-implement-the-wizard"></a>若要執行嚮導

1. 在 **ItemTemplateWizard** 專案中，開啟 **CustomActionWizard** 程式碼檔案，然後以下列程式碼取代此檔案中的目前程式碼：

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs" id="Snippet8":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 在本逐步解說的這個階段中，wizard 的所有程式碼現在都在專案中。 建立專案，以確定它會進行編譯而不會發生錯誤。

#### <a name="to-build-your-project"></a>建置您的專案

1. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

## <a name="associate-the-wizard-with-the-item-template"></a>建立 wizard 與專案範本的關聯
 現在您已完成嚮導，您必須完成三個主要步驟，將它與 **自訂動作** 專案範本產生關聯：

1. 使用強式名稱簽署嚮導元件。

2. 取得 wizard 元件的公開金鑰 token。

3. 在 **自訂動作** 專案範本的 .vstemplate 檔案中，加入 wizard 元件的參考。

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>使用強式名稱簽署 wizard 元件

1. 在 **方案總管** 中，開啟 **ItemTemplateWizard** 專案節點的快捷方式功能表，然後選擇 [ **屬性**]。

2. 在 [簽署] 索引標籤上，選取 [簽署組件] 核取方塊。

3. 在 [ **選擇強式名稱金鑰** 檔] 清單中，選擇 [] **\<New...>** 。

4. 在 [ **建立強式名稱金鑰** ] 對話方塊中，輸入名稱，清除 [ **以密碼保護我的金鑰** 檔案] 核取方塊，然後選擇 [ **確定]** 按鈕。

5. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>取得 wizard 元件的公開金鑰 token

1. 在 Visual Studio 的命令提示字元視窗中，執行下列命令，並將 *PathToWizardAssembly* 取代為開發電腦上 ItemTemplateWizard 專案之內建 ItemTemplateWizard.dll 元件的完整路徑。

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     *ItemTemplateWizard.dll* 元件的公開金鑰 token 會寫入 Visual Studio 命令提示字元視窗。

2. 讓 Visual Studio 的命令提示字元視窗保持開啟。 您將需要公開金鑰 token 才能完成下一個程式。

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>在 .vstemplate 檔案中加入 wizard 元件的參考

1. 在 **方案總管** 中，展開 [ **itemtemplate** ] 專案節點，然後開啟 *itemtemplate .vstemplate* 檔案。

2. 在檔案結尾附近， `WizardExtension` 于和標記之間新增下列元素 `</TemplateContent>` `</VSTemplate>` 。 將屬性的 *YourToken* 值取代 `PublicKeyToken` 為您在上一個程式中取得的公開金鑰 token。

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     如需專案的詳細資訊 `WizardExtension` ，請參閱 [&#40;Visual Studio 範本&#41;的 WizardExtension 元素 ](../extensibility/wizardextension-element-visual-studio-templates.md)。

3. 儲存並關閉檔案。

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>將可取代的參數新增至專案範本中的 *Elements.xml* 檔案
 在 ItemTemplate 專案的 *Elements.xml* 檔案中加入數個可取代的參數。 這些參數會在您稍 `PopulateReplacementDictionary` 早定義之類別的方法中初始化 `CustomActionWizard` 。 當使用者將自訂動作專案專案加入至專案時，Visual Studio 會自動將新專案專案中 *Elements.xml* 檔案中的這些參數取代為在 [wizard] 中指定的值。

 可取代的參數是以貨幣符號 ($) 字元開頭和結尾的標記。 除了定義您自己的可取代參數之外，您還可以使用 SharePoint 專案系統所定義和初始化的內建參數。 如需詳細資訊，請參閱可 [取代的參數](../sharepoint/replaceable-parameters.md)。

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>將可取代的參數新增至 *Elements.xml* 檔案

1. 在 ItemTemplate 專案中，以下列 XML 取代 *Elements.xml* 檔案的內容。

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

     新的 XML 會將 `Id` 、 `GroupId` 、 `Location` 、和屬性的值變更 `Description` `Url` 為可取代的參數。

2. 儲存並關閉檔案。

## <a name="add-the-wizard-to-the-vsix-package"></a>將嚮導新增至 VSIX 套件
 在 VSIX 專案的 extension.vsixmanifest 檔案中，加入 wizard 專案的參考，使其使用包含專案專案的 VSIX 套件進行部署。

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>將嚮導加入 VSIX 套件

1. 在 **方案總管** 中，從 CustomActionProjectItem 專案的 **extension.vsixmanifest** 檔案開啟快捷方式功能表，然後選擇 [ **開啟** ]，以在資訊清單編輯器中開啟檔案。

2. 在資訊清單編輯器中，選擇 [ **資產** ] 索引標籤，然後選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

3. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio**]。

4. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

5. 在 [ **專案** ] 清單中，選擇 [ **ItemTemplateWizard**]，然後選擇 [ **確定]** 按鈕。

6. 在功能表列上，選擇 [**組建**  >  **組建方案**]，然後確定方案會進行編譯而不會發生錯誤。

## <a name="test-the-wizard"></a>測試嚮導
 您現在已準備好測試 wizard。 首先，開始在 Visual Studio 的實驗實例中，對 CustomActionProjectItem 方案進行 debug 錯。 然後在 Visual Studio 的實驗實例中，針對 SharePoint 專案中的自訂動作專案專案，測試 wizard。 最後，建立並執行 SharePoint 專案，以驗證自訂動作是否如預期般運作。

#### <a name="to-start-to-debug-the-solution"></a>開始進行解決方案的調試

1. 使用系統管理認證重新開機 Visual Studio，然後開啟 CustomActionProjectItem 方案。

2. 在 ItemTemplateWizard 專案中，開啟 CustomActionWizard 程式碼檔案，然後將中斷點加入至方法中的第一行程式碼 `RunStarted` 。

3. 在功能表列上，選擇 [ **Debug**  >  **例外** 狀況]。

4. 在 [**例外** 狀況] 對話方塊中，確定已清除 [ **Common Language Runtime 例外** 狀況] 的 [擲回 **] 和 [** **使用者未處理**] 核取方塊，然後選擇 [**確定]** 按鈕。

5. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **開始調試** 程式]，以啟動偵錯工具。

     Visual Studio 將擴充功能安裝至%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 動作專案 Item\1.0，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-wizard-in-visual-studio"></a>若要在 Visual Studio 中測試嚮導

1. 在 Visual Studio 的實驗實例中 **，選擇功能表** 欄上的 [檔案  >  **新增**  >  **專案**]。

2. 展開 **Visual c #** 或 **Visual Basic** 節點 (根據您的專案範本支援的語言) ，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在專案範本清單中，選擇 [ **SharePoint 2010 專案**]，將專案命名為 **CustomActionWizardTest**，然後選擇 [ **確定]** 按鈕。

4. 在 [ **SharePoint 自訂嚮導]** 中，輸入您要用於偵錯工具的網站 URL，然後選擇 [ **完成]** 按鈕。

5. 在 **方案總管** 中，開啟專案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

6. 在 [ **加入新專案-CustomItemWizardTest** ] 對話方塊中，展開 [ **SharePoint** ] 節點，然後展開 **2010** 節點。

7. 在專案專案清單中，選擇 [ **自訂動作** ] 專案，然後選擇 [ **加入** ] 按鈕。

8. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早在此方法中設定的中斷點上停止 `RunStarted` 。

9. 選擇 **F5** 鍵或在功能表列上選擇 [ **debug** continue]，繼續進行專案的偵錯工具  >  ****。

      SharePoint 自訂精靈隨即出現。

10. 在 [ **位置**] 底下，選擇 [ **清單編輯** 選項] 按鈕。

11. 在 [ **群組識別碼** ] 清單中，選擇 [ **通訊**]。

12. 在 [ **標題** ] 方塊中，輸入 **SharePoint 開發人員中心**。

13. 在 [  **描述** ] 方塊中，輸入 **開啟 SharePoint 開發人員中心網站**。

14. 在 [ **URL** ] 方塊中，輸入 **https://docs.microsoft.com/sharepoint/dev/** ，然後選擇 [ **完成]** 按鈕。

     Visual Studio 會將名為 **CustomAction1** 的專案新增至您的專案，並在編輯器中開啟 *Elements.xml* 檔案。 確認 *Elements.xml* 包含您在嚮導中指定的值。

#### <a name="to-test-the-custom-action-in-sharepoint"></a>若要在 SharePoint 中測試自訂動作

1. 在 Visual Studio 的實驗實例中，選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug** 錯  >  **開始調試** 程式]。

     自訂動作會封裝並部署至專案的 [ **網站 URL** ] 屬性所指定的 SharePoint 網站，而網頁瀏覽器會開啟至此網站的預設頁面。

    > [!NOTE]
    > 如果出現 [ **腳本調試已停用** ] 對話方塊，請選擇 [ **是]** 按鈕。

2. 在 SharePoint 網站的 [清單] 區域中，選擇 **[工作]** 連結。

     [工作 **-所有** 工作] 頁面隨即出現。

3. 在功能區的 [ **清單工具** ] 索引標籤上，選擇 [ **清單** ] 索引標籤，然後在 [ **設定** ] 群組中選擇 [ **清單設定**]。

     [ **清單設定** ] 頁面隨即出現。

4. 在頁面頂端附近的 [ **通訊** ] 標題下，選擇 [ **SharePoint 開發人員中心** ] 連結，確認瀏覽器開啟網站 https://docs.microsoft.com/sharepoint/dev/ ，然後關閉瀏覽器。

## <a name="cleaning-up-the-development-computer"></a>清理開發電腦
 完成專案專案的測試之後，請從 Visual Studio 的實驗實例中移除專案專案範本。

#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**  >  **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [ **自訂動作] 專案** 專案延伸，然後選擇 [ **卸載** ] 按鈕。

3. 在出現的對話方塊中，選擇 [是] 按鈕，確認您要卸載擴充功能，然後選擇 [**立即重新開機** **]** 按鈕以完成卸載。

4. 關閉 Visual Studio 的兩個實例 (實驗實例，以及開啟 CustomActionProjectItem 方案) 的 Visual Studio 實例。

## <a name="see-also"></a>另請參閱
- [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
- [預設自訂動作位置和識別碼](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
