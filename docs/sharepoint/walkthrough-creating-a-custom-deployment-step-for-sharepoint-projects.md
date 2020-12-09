---
title: 建立 SharePoint 專案的自訂部署步驟
description: 在這個逐步解說中，建立自訂部署步驟，以在執行 SharePoint 的伺服器上升級 SharePoint 專案方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea8e6a09c512ed5edb6098183c66361e96537f54
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914929"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>逐步解說：建立 SharePoint 專案的自訂部署步驟
  當您部署 SharePoint 專案時，Visual Studio 會依特定循序執行一系列的部署步驟。 Visual Studio 包含許多內建的部署步驟，但您也可以建立自己的部署步驟。

 在這個逐步解說中，您將建立自訂部署步驟，以在執行 SharePoint 的伺服器上升級方案。 Visual Studio 包含許多工建的內建部署步驟，例如撤銷或新增解決方案，但不包含升級解決方案的部署步驟。 依預設，當您部署 SharePoint 方案時，Visual Studio 會先將方案 (撤銷，如果已部署) 然後重新部署整個方案。 如需內建部署步驟的詳細資訊，請參閱 [部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。

 本逐步解說將示範下列工作：

- 建立可執行兩個主要工作的 Visual Studio 延伸模組：

  - 此延伸模組定義了升級 SharePoint 方案的自訂部署步驟。

  - 延伸模組會建立定義新部署設定的專案延伸模組，這是針對指定專案執行的一組部署步驟。 新的部署設定包含自訂部署步驟和數個內建部署步驟。

- 建立兩個擴充元件呼叫的自訂 SharePoint 命令。 SharePoint 命令是可由擴充元件呼叫的方法，以在適用于 SharePoint 的伺服器物件模型中使用 Api。 如需詳細資訊，請參閱 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

- 建立 Visual Studio 擴充功能 (VSIX) 套件以部署這兩個元件。

- 測試新的部署步驟。

## <a name="prerequisites"></a>必要條件
 您需要在開發電腦上執行下列元件，才能完成此逐步解說：

- 支援的 Windows、SharePoint 和 Visual Studio 版本。

- Visual Studio SDK。 本逐步解說會使用 SDK 中的 **Vsix 專案** 範本來建立 vsix 封裝，以部署擴充功能。 如需詳細資訊，請參閱 [Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成此逐步解說：

- 使用 SharePoint 的伺服器物件模型。 如需詳細資訊，請參閱 [使用 SharePoint Foundation Server-Side 物件模型](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14))。

- SharePoint 方案。 如需詳細資訊，請參閱 [解決方案總覽](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14))。

- 升級 SharePoint 方案。 如需詳細資訊，請參閱 [升級方案](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14))。

## <a name="create-the-projects"></a>建立專案
 若要完成這個逐步解說，您必須建立三個專案：

- 建立 VSIX 封裝以部署擴充功能的 VSIX 專案。

- 實擴充的類別庫專案。 這個專案必須以 .NET Framework 4.5 為目標。

- 定義自訂 SharePoint 命令的類別庫專案。 這個專案必須以 .NET Framework 3.5 為目標。

  藉由建立專案來開始逐步解說。

#### <a name="to-create-the-vsix-project"></a>建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

3. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [擴充性 **] 節點。**

    > [!NOTE]
    > 只有當您安裝 Visual Studio SDK 時，才能使用擴充 **性節點。** 如需詳細資訊，請參閱本主題稍早的必要條件一節。

4. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 4.5** 。

5. 選擇 [ **VSIX 專案** ] 範本、將專案命名為 **UpgradeDeploymentStep**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **UpgradeDeploymentStep** 專案新增至 **方案總管**。

#### <a name="to-create-the-extension-project"></a>建立延伸模組專案

1. 在 **方案總管** 中，開啟 [UpgradeDeploymentStep] 方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [ **Windows** ] 節點。

3. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 4.5** 。

4. 選擇 [ **類別庫** ] 專案範本、將專案命名為 **DeploymentStepExtension**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **DeploymentStepExtension** 專案加入至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

#### <a name="to-create-the-sharepoint-command-project"></a>若要建立 SharePoint 命令專案

1. 在 **方案總管** 中，開啟 [UpgradeDeploymentStep] 方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic**]，然後選擇 [ **Windows** ] 節點。

3. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 3.5** 。

4. 選擇 [ **類別庫** ] 專案範本、將專案命名為 **SharePointCommands**，然後選擇 [ **確定]** 按鈕。

     Visual Studio 將 **SharePointCommands** 專案新增至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-projects"></a>設定專案
 撰寫程式碼以建立自訂部署步驟之前，您必須加入程式碼檔案和元件參考，而且必須設定專案。

#### <a name="to-configure-the-deploymentstepextension-project"></a>設定 DeploymentStepExtension 專案

1. 在 **DeploymentStepExtension** 專案中，新增兩個具有下列名稱的程式碼檔案：

    - UpgradeStep

    - DeploymentConfigurationExtension

2. 開啟 DeploymentStepExtension 專案的快捷方式功能表，然後選擇 [ **加入參考**]。

3. 在 [ **Framework** ] 索引標籤上，選取 [ComponentModel] 元件的核取方塊。

4. 在 [ **擴充** 功能] 索引標籤上，選取 [VisualStudio] 元件的核取方塊，然後選擇 [ **確定]** 按鈕。

#### <a name="to-configure-the-sharepointcommands-project"></a>設定 SharePointCommands 專案

1. 在 **SharePointCommands** 專案中，加入名為命令的程式碼檔案。

2. 在 **方案總管** 中，開啟 **SharePointCommands** 專案節點的快捷方式功能表，然後選擇 [ **加入參考**]。

3. 在 [ **擴充** 功能] 索引標籤上，選取下列元件的核取方塊，然後按一下 [ **確定]** 按鈕。

    - Microsoft SharePoint

    - VisualStudio 命令

## <a name="define-the-custom-deployment-step"></a>定義自訂部署步驟
 建立定義升級部署步驟的類別。 為了定義部署步驟，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 介面。 當您想要定義自訂部署步驟時，請執行這個介面。

#### <a name="to-define-the-custom-deployment-step"></a>若要定義自訂部署步驟

1. 在 **DeploymentStepExtension** 專案中，開啟 UpgradeStep 程式碼檔案，然後將下列程式碼貼入其中。

    > [!NOTE]
    > 當您加入此程式碼之後，專案將會有一些編譯錯誤，但是當您在後續步驟中新增程式碼時，就會消失。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>建立包含自訂部署步驟的部署設定
 建立新部署設定的專案擴充功能，其中包含數個內建的部署步驟和新的升級部署步驟。 藉由建立此延伸模組，您可以説明 SharePoint 開發人員在 SharePoint 專案中使用升級部署步驟。

 若要建立部署設定，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面。 當您想要建立 SharePoint 專案延伸模組時，請執行這個介面。

#### <a name="to-create-the-deployment-configuration"></a>建立部署設定

1. 在 **DeploymentStepExtension** 專案中，開啟 DeploymentConfigurationExtension 程式碼檔案，然後將下列程式碼貼入其中。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>建立自訂 SharePoint 命令
 建立兩個自訂命令，以呼叫 SharePoint 的伺服器物件模型。 一個命令可判斷是否已部署解決方案;另一個命令會升級方案。

#### <a name="to-define-the-sharepoint-commands"></a>若要定義 SharePoint 命令

1. 在 **SharePointCommands** 專案中，開啟命令程式碼檔，然後將下列程式碼貼入其中。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>Checkpoint
 在本逐步解說的這個階段中，自訂部署步驟和 SharePoint 命令的所有程式碼現在都位於專案中。 建立它們，以確保它們在沒有錯誤的情況下進行編譯。

#### <a name="to-build-the-projects"></a>若要建立專案

1. 在 **方案總管** 中，開啟 **DeploymentStepExtension** 專案的快捷方式功能表，然後選擇 [ **組建**]。

2. 開啟 **SharePointCommands** 專案的快捷方式功能表，然後選擇 [ **建立**]。

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 套件以部署擴充功能
 若要部署擴充功能，請在您的方案中使用 VSIX 專案來建立 VSIX 套件。 首先，藉由修改 VSIX 專案中的 extension.vsixmanifest 檔案來設定 VSIX 套件。 然後藉由建立解決方案來建立 VSIX 套件。

#### <a name="to-configure-and-create-the-vsix-package"></a>設定和建立 VSIX 封裝

1. 在 **方案總管** 的 [ **UpgradeDeploymentStep** ] 專案底下，開啟 **extension.vsixmanifest** 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     Visual Studio 在資訊清單編輯器中開啟檔案。 Extension.vsixmanifest 檔案是所有 VSIX 封裝所需的 extension.vsixmanifest 檔案基礎。 如需此檔案的詳細資訊，請參閱 [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))。

2. 在 [ **產品名稱** ] 方塊中，輸入 **SharePoint 專案的升級部署步驟**。

3. 在 [ **作者** ] 方塊中，輸入 **Contoso**。

4. 在 [ **描述** ] 方塊中，輸入 **可提供可在 SharePoint 專案中使用的自訂升級部署步驟**。

5. 在編輯器的 [ **資產** ] 索引標籤中，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

6. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

    > [!NOTE]
    > 此值對應至 `MefComponent` extension.vsixmanifest 檔案中的元素。 這個元素會指定 VSIX 封裝中的擴充元件名稱。 如需詳細資訊，請參閱 [[Microsoft.visualstudio.mefcomponent] 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

7. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

8. 在 [ **專案** ] 清單中，選擇 [ **DeploymentStepExtension**]，然後選擇 [ **確定]** 按鈕。

9. 在資訊清單編輯器中，再次選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

10. 在 [ **類型** ] 清單中，輸入 [ **SharePoint**]。

    > [!NOTE]
    > 這個元素會指定您想要包含在 Visual Studio 延伸模組中的自訂擴充功能。 如需詳細資訊，請參閱 [資產元素 (VSX 架構) ](/previous-versions/dd393737(v=vs.110))。

11. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

12. 在 [ **專案** ] 清單中，選擇 [ **SharePointCommands**]，然後選擇 [ **確定]** 按鈕。

13. 在功能表列上，選擇 [**組建**  >  **組建方案**]，然後確定方案會進行編譯而不會發生錯誤。

14. 請確定 UpgradeDeploymentStep 專案的組建輸出檔案夾現在包含 UpgradeDeploymentStep .vsix 檔案。

     根據預設，組建輸出檔案夾為。包含您專案檔之資料夾下的 \bin\Debug 資料夾。

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>準備測試升級部署步驟
 若要測試升級部署步驟，您必須先將範例方案部署到 SharePoint 網站。 首先，請先在 Visual Studio 的實驗實例中，對擴充功能進行偵錯工具。 然後建立清單定義和清單實例，以用來測試部署步驟，然後將它們部署到 SharePoint 網站。 接下來，修改清單定義和清單實例並重新部署，以示範預設部署程式如何覆寫 SharePoint 網站上的方案。

 稍後在此逐步解說中，您將修改清單定義和清單實例，然後在 SharePoint 網站上進行升級。

#### <a name="to-start-debugging-the-extension"></a>開始進行擴充功能的調試

1. 使用系統管理認證重新開機 Visual Studio，然後開啟 UpgradeDeploymentStep 方案。

2. 在 DeploymentStepExtension 專案中，開啟 UpgradeStep 程式碼檔案，然後將中斷點加入至和方法中的第一行程式碼 `CanExecute` `Execute` 。

3. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **開始調試** 程式]，以開始進行偵錯工具。

4. Visual Studio 將擴充功能安裝到 SharePoint Projects\1.0 的%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 部署步驟，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的此實例中測試升級部署步驟。

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>若要建立具有清單定義和清單實例的 SharePoint 專案

1. 在 Visual Studio 的實驗實例中 **，選擇功能表** 欄上的 [檔案  >  **新增**  >  **專案**]。

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 節點或 [ **Visual Basic** ] 節點，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在對話方塊的頂端，確定 .NET Framework 的版本清單中出現 **.NET Framework 3.5** 。

    的專案 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 需要這個版本的 .NET Framework。

4. 在專案範本清單中，選擇 [ **SharePoint 2010 專案**]，將專案命名為 **EmployeesListDefinition**，然後選擇 [ **確定]** 按鈕。

5. 在 [ **SharePoint 自訂嚮導]** 中，輸入您要用於偵錯工具的網站 URL。

6. 在 [ **此 SharePoint 方案的信任層級是什麼**] 下，選擇 [ **部署為數組方案** ] 選項按鈕。

   > [!NOTE]
   > 升級部署步驟不支援沙箱化解決方案。

7. 選擇 [完成] 按鈕。

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立 EmployeesListDefinition 專案。

8. 開啟 EmployeesListDefinition 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

9. 在 [ **加入新專案-EmployeesListDefinition** ] 對話方塊中，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

10. 選擇 [ **清單** 專案] 範本、將專案命名為 [ **員工] 清單**，然後選擇 [ **加入** ] 按鈕。

     [SharePoint 自訂] Wizard 隨即出現

11. 在 [ **挑選清單設定** ] 頁面上，確認下列設定，然後選擇 [ **完成]** 按鈕：

    1. **員工清單** 會出現在 [ **您想要為清單顯示什麼名稱？** ] 方塊中。

    2. 選擇 [ **建立依據下列選項的可自訂清單** ] 選項按鈕。

    3. **預設 (空白)** 是在 [ **建立可自訂的清單依據：** ] 清單中選擇。

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立具有標題資料行和單一空白實例的員工清單專案，然後開啟清單設計工具。

12. 在 **[清單設計工具] 的** [資料行] 索引標籤上，選擇 [ **輸入新的或現有的** 資料行名稱] 資料列，然後在 [資料行 **顯示名稱** ] 清單中新增下列資料行：

    1. 名字

    2. 公司

    3. 公司電話

    4. 電子郵件

13. 儲存所有檔案，然後關閉清單設計工具。

14. 在 **方案總管** 中，展開 [ **員工清單** ] 節點，然後展開 [ **員工] 清單實例** 子節點。

15. 在 *Elements.xml* 檔案中，將此檔案中的預設 xml 取代為下列 xml。 此 XML 會將清單的名稱變更為 **員工** ，並為名為 Jim Hance 的員工新增資訊。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
        <Data>
          <Rows>
            <Row>
              <Field Name="Title">Hance</Field>
              <Field Name="FirstName">Jim</Field>
              <Field Name="Company">Contoso</Field>
              <Field Name="Business Phone">555-555-5555</Field>
              <Field Name="E-Mail">jim@contoso.com</Field>
            </Row>
          </Rows>
        </Data>
      </ListInstance>
    </Elements>
    ```

16. 儲存並關閉 *Elements.xml* 檔案。

17. 開啟 EmployeesListDefinition 專案的快捷方式功能表，然後選擇 [ **開啟** ] 或 [ **屬性**]。

     [屬性設計工具] 隨即開啟。

18. 在 [ **SharePoint** ] 索引標籤上，清除 [ **在調試後自動** 撤銷] 核取方塊，然後儲存屬性。

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>部署清單定義和清單實例

1. 在 **方案總管** 中，選擇 [ **EmployeesListDefinition** ] 專案節點。

2. 在 [ **屬性** ] 視窗中，確定 [ **主動式部署** 設定] 屬性設定為 [ **預設**]。

3. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug** 錯  >  **開始調試**]。

4. 確認專案已成功建立，網頁瀏覽器會開啟至 SharePoint 網站，快速啟動列中的 **清單** 專案包含新的 **員工** 清單，且 **員工** 清單中包含 Jim Hance 的專案。

5. 關閉網頁瀏覽器。

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>修改清單定義和清單實例並重新部署

1. 在 EmployeesListDefinition 專案中，開啟 *Elements.xml* 的檔案，該檔案是 **員工清單實例** 專案專案的子專案。

2. 移除 `Data` 專案及其子系，以從清單中移除 Jim Hance 的專案。

     當您完成時，檔案應該包含下列 XML。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
      </ListInstance>
    </Elements>
    ```

3. 儲存並關閉 *Elements.xml* 檔案。

4. 開啟 **Employees 清單** 專案專案的快捷方式功能表，然後選擇 [ **開啟** ] 或 [ **屬性**]。

5. 在 [清單設計工具] 中，選擇 [ **流覽** ] 索引標籤。

6. 在 [ **選取** 的資料行] 清單中，選擇 [ **附件**]，然後選擇 < 索引鍵，將該資料行移至 [可用的資料 **行** ] 清單。

7. 重複上述步驟，將 [ **Business Phone** ] 資料行從 [ **選取** 的資料行] 清單移至 [可用的資料 **行** ] 清單。

     此動作會從 SharePoint 網站上 [ **員工** ] 清單的預設視圖中移除這些欄位。

8. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **開始調試** 程式]，以開始進行偵錯工具。

9. 確認 [ **部署衝突** ] 對話方塊隨即出現。

     當 Visual Studio 嘗試部署方案時，會出現此對話方塊， (清單實例) 至已部署該方案的 SharePoint 網站。 當您稍後在本逐步解說中執行升級部署步驟時，不會出現此對話方塊。

10. 在 [ **部署衝突** ] 對話方塊中，選擇 [ **自動解決** ] 選項按鈕。

     Visual Studio 刪除 SharePoint 網站上的清單實例、在專案中部署清單專案，然後開啟 SharePoint 網站。

11. 在快速啟動 **列** 的 [清單] 區段中，選擇 [ **員工** ] 清單，然後確認下列詳細資料：

    - [ **附件** ] 和 [ **家庭電話** ] 資料行不會出現在清單的此視圖中。

    - 清單是空的。 當您使用 **預設** 部署設定重新部署方案時，會以專案中新的空白清單取代 **員工** 清單。

## <a name="test-the-deployment-step"></a>測試部署步驟
 您現在已準備好測試升級部署步驟。 首先，將專案加入至 SharePoint 中的清單實例。 然後變更清單定義和清單實例，並在 SharePoint 網站上升級，並確認升級部署步驟不會覆寫新的專案。

#### <a name="to-manually-add-an-item-to-the-list"></a>手動將專案加入至清單

1. 在 SharePoint 網站上的功能區中，于 [ **清單工具** ] 索引標籤下，選擇 [ **專案** ] 索引標籤。

2. 在 [ **新增** ] 群組中，選擇 [ **新增專案**]。

     或者，您也可以選擇專案清單本身的 [ **加入新專案** ] 連結。

3. 在 [ **員工-新增專案** ] 視窗的 [ **標題** ] 方塊中，輸入 [ **裝置管理員**]。

4. 在 [ **名字** ] 方塊中， **輸入 [** 名稱]。

5. 在 [ **公司** ] 方塊中，輸入 **Contoso**。

6. 選擇 [ **儲存** ] 按鈕，確認新專案出現在清單中，然後關閉 web 瀏覽器。

     稍後在此逐步解說中，您將使用此專案來確認升級部署步驟不會覆寫此清單的內容。

#### <a name="to-test-the-upgrade-deployment-step"></a>測試升級部署步驟

1. 在 Visual Studio 的實驗實例中，于 **方案總管** 開啟 **EmployeesListDefinition** 專案節點的快捷方式功能表，然後選擇 [ **屬性**]。

    [屬性編輯器]/[設計工具] 隨即開啟。

2. 在 [ **SharePoint** ] 索引標籤上，將 [ **現用部署** 設定] 屬性設定為 [ **升級**]。

    此自訂部署設定包含新的升級部署步驟。

3. 開啟 **Employees 清單** 專案專案的快捷方式功能表，然後選擇 [ **屬性** ] 或 [ **開啟**]。

    [屬性編輯器]/[設計工具] 隨即開啟。

4. 在 [ **流覽** ] 索引標籤上，選擇 [ **電子郵件** ] 資料行，然後選擇 **<** 要將該資料行從 [選取的資料 **行** ] 清單移至 [可用的資料 **行** ] 清單的

    此動作會從 SharePoint 網站上 [ **員工** ] 清單的預設視圖中移除這些欄位。

5. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **開始調試** 程式]，以開始進行偵錯工具。

6. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早在此方法中設定的中斷點上停止 `CanExecute` 。

7. 再次選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **Continue**]。

8. 確認程式碼在您稍早在此方法中設定的中斷點上停止 `Execute` 。

9. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **Continue** ] （最後一次）。

     Web 瀏覽器會開啟 SharePoint 網站。

10. 在 [快速啟動] 區域的 [ **清單** ] 區段中，選擇 [ **員工** ] 清單，然後確認下列詳細資料：

    - 您以手動方式新增的專案 (，裝置管理員) 仍在清單中。

    - [ **公司電話** ] 和 [ **電子郵件地址** ] 欄位不會出現在清單的此視圖中。

      **升級** 部署設定會修改 SharePoint 網站上的現有 **員工** 清單實例。 如果您使用 **預設** 部署設定，而不是 **升級** 設定，則會遇到部署衝突。 Visual Studio 會藉由取代 **員工** 清單來解決衝突，而裝置管理員的專案則會被刪除。

## <a name="clean-up-the-development-computer"></a>清除開發電腦
 完成升級部署步驟的測試之後，請從 SharePoint 網站移除清單實例和清單定義，然後從 Visual Studio 移除部署步驟延伸模組。

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>從 SharePoint 網站移除清單實例

1. 如果清單尚未開啟，請開啟 SharePoint 網站上的 [ **員工** ] 清單。

2. 在 SharePoint 網站上的功能區中，選擇 [ **清單工具** ] 索引標籤，然後選擇 [ **清單** ] 索引標籤。

3. 在 [ **設定** ] 群組中，選擇 [ **清單設定** ] 專案。

4. 在 [ **許可權與管理**] 之下，選擇 [ **刪除此清單** ] 命令，選擇 **[確定]** 以確認您要將清單傳送至資源回收筒，然後關閉網頁瀏覽器。

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>從 SharePoint 網站移除清單定義

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**組建** 撤銷]  >  ****。

     Visual Studio 從 SharePoint 網站收回清單定義。

#### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**  >  **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [ **SharePoint 專案的升級部署步驟**]，然後選擇 [ **卸載** ] 命令。

3. 在出現的對話方塊中，選擇 [ **是]** 以確認您要卸載擴充功能，然後選擇 [ **立即重新開機** ] 以完成卸載。

4. 關閉 Visual Studio 的兩個實例 (實驗實例，以及開啟 UpgradeDeploymentStep 方案) 的 Visual Studio 實例。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)