---
title: 逐步解說：建立 SharePoint 專案的自訂部署步驟 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: ece85279e4ecff20eff0a79c75f4f316de1a54cf
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609393"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>逐步解說：建立 SharePoint 專案的自訂部署步驟
  當您部署 SharePoint 專案時，Visual Studio 會以特定順序執行一系列的部署步驟。 Visual Studio 包含許多的內建的部署步驟，但您也可以建立您自己。

 在本逐步解說中，您將建立的自訂部署步驟，以升級執行 SharePoint 的伺服器上的解決方案。 Visual Studio 包含許多工作，這類撤銷或新增解決方案，內建的部署步驟，但它不包含升級方案的部署步驟。 根據預設，當您部署 SharePoint 方案，Visual Studio 先撤銷方案 （如果已部署），並再重新部署整個解決方案。 如需有關內建的部署步驟的詳細資訊，請參閱 <<c0> [ 部署、 發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。

 本逐步解說將示範下列工作：

-   建立 Visual Studio 擴充功能可執行兩項主要工作：

    -   延伸模組會定義以升級 SharePoint 方案的自訂部署步驟。

    -   延伸模組建立專案延伸模組，可定義新的部署設定，這是一組會針對指定的專案執行的部署步驟。 新的部署組態包括自訂部署步驟和數個內建的部署步驟。

-   建立兩個延伸模組組件呼叫的自訂 SharePoint 命令。 SharePoint 命令是使用伺服器物件模型中的 Api，適用於 SharePoint 的延伸模組組件可以呼叫的方法。 如需詳細資訊，請參閱 <<c0> [ 呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

-   建置 Visual Studio 擴充功能 (VSIX) 封裝來部署這兩個組件。

-   測試新的部署步驟。

## <a name="prerequisites"></a>必要條件
 您需要完成這個逐步解說在開發電腦上的下列元件：

- 支援的 Windows、 SharePoint 和 Visual Studio 版本。

- Visual Studio SDK 中。 本逐步解說會使用**VSIX 專案**建立 VSIX 封裝，來部署擴充功能 SDK 中的範本。 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識會很有幫助，但並非必要，若要完成本逐步解說：

- 使用適用於 SharePoint 的伺服器物件模型。 如需詳細資訊，請參閱 <<c0> [ 使用 SharePoint Foundation 伺服器端物件模型](http://go.microsoft.com/fwlink/?LinkId=177796)。

- SharePoint 方案。 如需詳細資訊，請參閱 <<c0> [ 解決方案概觀](http://go.microsoft.com/fwlink/?LinkId=169422)。

- 升級 SharePoint 方案。 如需詳細資訊，請參閱 <<c0> [ 升級解決方案](http://go.microsoft.com/fwlink/?LinkId=177802)。

## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說中，您必須建立三個專案：

- 若要建立 VSIX 封裝，來部署擴充功能的 VSIX 專案。

- 實作延伸的類別庫專案。 此專案必須以.NET Framework 4.5 為目標。

- 定義自訂的 SharePoint 命令的類別庫專案。 此專案必須以.NET Framework 3.5 為目標。

  開始本逐步解說建立的專案。

#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案

1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2.  在功能表列上，選擇 [檔案] > [新增] > [專案]。

3.  中**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**擴充性**節點。

    > [!NOTE]
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。

4.  在對話方塊頂端，選擇 **.NET Framework 4.5**清單中的.NET Framework 版本。

5.  選擇**VSIX 專案**範本，將專案命名為**UpgradeDeploymentStep**，然後選擇**確定** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**UpgradeDeploymentStep**專案加入**方案總管 中**。

#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案

1.  中**方案總管**，開啟 UpgradeDeploymentStep 方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。

2.  中**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**Windows**節點。

3.  在對話方塊頂端，選擇 **.NET Framework 4.5**清單中的.NET Framework 版本。

4.  選擇**類別庫**專案範本，請將專案命名**DeploymentStepExtension**，然後選擇**確定** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**DeploymentStepExtension**專案加入方案，並開啟預設 Class1 的程式碼檔案。

5.  從專案刪除 Class1 的程式碼檔案。

#### <a name="to-create-the-sharepoint-command-project"></a>若要建立 SharePoint 命令專案

1.  中**方案總管**，開啟 UpgradeDeploymentStep 方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。

2.  在**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**，然後選擇**Windows**節點。

3.  在對話方塊頂端，選擇 **.NET Framework 3.5**清單中的.NET Framework 版本。

4.  選擇**類別庫**專案範本，請將專案命名**SharePointCommands**，然後選擇**確定** 按鈕。

     Visual Studio 會加入**SharePointCommands**專案加入方案，並開啟預設 Class1 的程式碼檔案。

5.  從專案刪除 Class1 的程式碼檔案。

## <a name="configure-the-projects"></a>將專案設定
 您撰寫程式碼來建立自訂部署步驟之前，您必須新增程式碼檔案和組件參考，而且您必須設定專案。

#### <a name="to-configure-the-deploymentstepextension-project"></a>若要設定 DeploymentStepExtension 專案

1.  在  **DeploymentStepExtension**專案中，加入兩個具有下列名稱的程式碼檔案：

    -   UpgradeStep

    -   DeploymentConfigurationExtension

2.  開啟 DeploymentStepExtension 專案的捷徑功能表，然後選擇**加入參考**。

3.  在  **Framework**索引標籤上，選取核取方塊，針對 System.ComponentModel.Composition 組件。

4.  在 [**延伸模組**索引標籤上的 Microsoft.VisualStudio.SharePoint 組件中，選取核取方塊，然後選擇**確定**] 按鈕。

#### <a name="to-configure-the-sharepointcommands-project"></a>若要設定 SharePointCommands 專案

1.  在  **SharePointCommands**專案中，加入名為命令的程式碼檔案。

2.  在 [**方案總管] 中**，開啟捷徑功能表上**SharePointCommands**專案節點，然後選擇**加入參考**。

3.  在 **延伸模組**索引標籤上，選取下列組件中，核取方塊，然後按一下 選擇**確定**按鈕

    -   Microsoft.SharePoint

    -   Microsoft.VisualStudio.SharePoint.Commands

## <a name="define-the-custom-deployment-step"></a>定義自訂部署步驟
 建立一個類別來定義升級的部署步驟。 若要定義部署步驟，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>介面。 每當您想要定義的自訂部署步驟，請實作這個介面。

#### <a name="to-define-the-custom-deployment-step"></a>若要定義自訂部署步驟

1.  在  **DeploymentStepExtension**專案，開啟 UpgradeStep 程式碼檔案，然後將下列程式碼貼到它。

    > [!NOTE]
    >  新增下列程式碼，專案會有某些編譯錯誤，但它們就會消失之後當您加入程式碼在稍後的步驟。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>建立部署組態，包括自訂部署步驟
 建立新的部署組態，其中包含數個內建的部署步驟和新的升級部署步驟的專案延伸模組。 藉由建立此延伸模組，您可以協助 SharePoint 開發人員在 SharePoint 專案中使用升級的部署步驟。

 若要建立的部署組態，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>介面。 每當您想要建立 SharePoint 專案擴充功能，請實作這個介面。

#### <a name="to-create-the-deployment-configuration"></a>若要建立的部署組態

1.  在  **DeploymentStepExtension**專案，開啟 DeploymentConfigurationExtension 程式碼檔案，然後將下列程式碼貼到它。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>建立自訂的 SharePoint 命令
 建立兩個呼叫伺服器物件模型，適用於 SharePoint 的自訂命令。 一個命令會判斷是否已部署方案;另一個命令會將升級解決方案。

#### <a name="to-define-the-sharepoint-commands"></a>若要定義的 SharePoint 命令

1.  在  **SharePointCommands**專案，開啟指令碼檔案，然後將下列程式碼貼到它。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>檢查點
 此時在逐步解說中，自訂部署步驟和 SharePoint 命令的所有程式碼已在專案中。 建置，以確保它們編譯無誤。

#### <a name="to-build-the-projects"></a>若要建置的專案

1.  在 [**方案總管] 中**，開啟捷徑功能表**DeploymentStepExtension**專案，，然後選擇**建置**。

2.  開啟捷徑功能表**SharePointCommands**專案，，然後選擇**建置**。

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 封裝，來部署擴充功能
 若要建立 VSIX 封裝部署擴充功能，請在解決方案中使用 VSIX 專案。 首先，設定 VSIX 套件藉由修改 source.extension.vsixmanifest 檔案中的，在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。

#### <a name="to-configure-and-create-the-vsix-package"></a>若要設定及建立 VSIX 封裝

1.  在 **方案總管 中**下方**UpgradeDeploymentStep**專案中，開啟捷徑功能表**source.extension.vsixmanifest**檔案，然後再選擇  **開啟**。

     Visual Studio 會在資訊清單編輯器中開啟檔案。 Source.extension.vsixmanifest 檔案中會是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱 < [VSIX 延伸結構描述 1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。

2.  在  **Product Name**方塊中，輸入**升級 SharePoint 專案的部署步驟**。

3.  在 **作者**方塊中，輸入**Contoso**。

4.  在 **描述**方塊中，輸入**提供可用在 SharePoint 專案的自訂升級的部署步驟**。

5.  在 **資產** 索引標籤的編輯器中，選擇**新增** 按鈕。

     **加入新資產** 對話方塊隨即出現。

6.  在 **型別**清單中，選擇**Microsoft.VisualStudio.MefComponent**。

    > [!NOTE]
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個元素會指定在 VSIX 封裝中的延伸模組組件名稱。 如需詳細資訊，請參閱 < [MEFComponent 項目 （VSX 結構描述）](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

7.  在 **來源**清單中，選擇**目前方案中的專案**。

8.  在 [**專案**清單中，選擇**DeploymentStepExtension**，然後選擇 **[確定]** ] 按鈕。

9. 在資訊清單編輯器中，選擇**新增**按鈕一次。

     **加入新資產** 對話方塊隨即出現。

10. 在 **型別**清單中，輸入**SharePoint.Commands.v4**。

    > [!NOTE]
    >  這個元素會指定您想要包含在 Visual Studio 擴充功能的自訂延伸模組。 如需詳細資訊，請參閱 <<c0> [ 資產項目 （VSX 結構描述）](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)。

11. 在 **來源**清單中，選擇**目前方案中的專案**。

12. 在 [**專案**清單中，選擇**SharePointCommands**，然後選擇 **[確定]** ] 按鈕。

13. 在功能表列上選擇 **建置** > **建置方案**，然後確認方案編譯無誤。

14. 請確定 UpgradeDeploymentStep 專案建置輸出資料夾現在包含 UpgradeDeploymentStep.vsix 檔案。

     根據預設，會將組建輸出資料夾...在包含您的專案檔的資料夾下的 \bin\Debug 資料夾。

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>準備測試升級的部署步驟
 若要測試升級的部署步驟，您必須先部署範例方案的 SharePoint 網站。 開始偵錯 Visual Studio 的實驗執行個體中的擴充功能。 接著建立清單定義和清單執行個體，用來測試部署步驟，並再將其部署至 SharePoint 網站。 接下來，修改清單定義和清單執行個體，並重新部署這些示範如何在預設部署程序會覆寫在 SharePoint 網站上的解決方案。

 稍後在本逐步解說中，您將修改的清單定義和清單執行個體，並接著您會將它們升級 SharePoint 網站上。

#### <a name="to-start-debugging-the-extension"></a>若要開始偵錯擴充功能

1.  使用系統管理認證，重新啟動 Visual Studio，然後開啟 UpgradeDeploymentStep 解決方案。

2.  在 DeploymentStepExtension 專案中，開啟 UpgradeStep 程式碼檔案，然後加入中斷點至第一行中的程式碼`CanExecute`和`Execute`方法。

3.  開始偵錯選擇**F5**金鑰或，功能表列選擇**偵錯** > **開始偵錯**。

4.  Visual Studio 會 SharePoint Projects\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 部署步驟安裝擴充功能，並啟動 Visual Studio 的實驗執行個體。 您將在 Visual Studio 這個執行個體中測試升級的部署步驟。

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>若要使用的清單定義和清單執行個體中建立 SharePoint 專案

1. 在實驗性 Visual Studio 執行個體，在功能表列上，選擇**檔案** > **新增** > **專案**。

2. 中**新的專案**對話方塊方塊中，展開**Visual C#** 節點或**Visual Basic**  節點，展開**SharePoint**  節點，然後選擇 **2010年**節點。

3. 在對話方塊頂端，確定 **.NET Framework 3.5**會出現在.NET Framework 版本的清單。

    專案[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]需要這個版本的.NET Framework。

4. 在專案範本清單中，選擇**SharePoint 2010 專案**，將專案命名**EmployeesListDefinition**，然後選擇**確定**  按鈕。

5. 在  **SharePoint 自訂精靈**，輸入您想要用於偵錯的網站 URL。

6. 底下**此 SharePoint 方案的信任層級為何**，選擇**部署為伺服陣列方案**選項按鈕。

   > [!NOTE]
   >  升級的部署步驟不支援沙箱化方案。

7. 選擇**完成** 按鈕。

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立 EmployeesListDefinition 專案。

8. 開啟 EmployeesListDefinition 專案的捷徑功能表，選擇 **新增**，然後選擇**新項目**。

9. 在**加入新項目-EmployeesListDefinition**對話方塊方塊中，展開**SharePoint**節點，然後選擇**2010年**節點。

10. 選擇**清單**項目範本、 項目命名**員工清單**，然後選擇**新增** 按鈕。

     SharePoint 自訂精靈 隨即出現

11. 在 **選擇清單設定**頁面上，確認下列設定，然後選擇**完成**按鈕：

    1. **員工清單**會出現在**您想要讓清單顯示什麼名稱？**  方塊中。

    2. **建立可自訂的清單為基礎：** 選擇選項按鈕。

    3. **預設值 （空白）** 中選擇**建立可自訂的清單為基礎：** 清單。

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立員工清單項目具有標題資料行和單一的空執行個體，並開啟清單設計工具。

12. 在清單設計工具中上,**資料行**索引標籤上，選擇**新的或現有的資料行名稱**資料列，，，然後加入下列中的資料行**資料行的顯示名稱**清單：

    1.  名字

    2.  公司

    3.  公司電話

    4.  電子郵件

13. 儲存所有檔案，然後再關閉 清單設計工具。

14. 中**方案總管**，展開**員工清單**節點，然後展開**員工清單執行個體**子節點。

15. 在  *Elements.xml*檔案中，以下列 XML 取代預設的 此檔案中的 XML。 這段 XML 會變更的清單名稱**員工**並新增名為 Jim 宗翰的員工的資訊。

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

16. 儲存並關閉*Elements.xml*檔案。

17. 開啟 EmployeesListDefinition 專案的捷徑功能表，然後選擇**開放**或是**屬性**。

     屬性設計工具隨即開啟。

18. 在  **SharePoint**索引標籤上，清除**偵錯後自動撤銷**核取方塊，並再儲存屬性。

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>若要部署的清單定義和清單執行個體

1.  在 **方案總管**，選擇**EmployeesListDefinition**專案節點。

2.  在 [**屬性**] 視窗中，請確定**現用部署組態**屬性設定為**預設**。

3.  選擇**F5**鍵，或在功能表列上選擇 **偵錯** > **開始偵錯**。

4.  確認專案建置成功，網頁瀏覽器會開啟 SharePoint 網站，**列出**快速啟動 列中的項目會包含新**員工**清單中，而且**員工**Jim 宗翰清單包含項目。

5.  關閉網頁瀏覽器。

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>若要修改的清單定義和清單執行個體，並重新部署

1.  在 EmployeesListDefinition 專案中，開啟*Elements.xml*子系的檔案**員工清單執行個體**專案項目。

2.  移除`Data`元素和其子系的 Jim 宗翰中移除項目，從清單中。

     當您完成時，此檔案應包含下列 XML 程式碼。

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

3.  儲存並關閉*Elements.xml*檔案。

4.  開啟捷徑功能表**員工清單**項目時，專案，然後選擇**開放**或是**屬性**。

5.  在清單設計工具中，選擇**檢視** 索引標籤。

6.  在**選取的資料行**清單中，選擇**附件**，然後選擇 < 鍵來移至該資料行**可用的資料行**清單。

7.  重複上述步驟來移動**公司電話**資料行**選取的資料行**若要列出**可用的資料行**清單。

     此動作會移除的預設檢視中的這些欄位**員工**SharePoint 網站上的清單。

8.  開始偵錯選擇**F5**金鑰或，功能表列選擇**偵錯** > **開始偵錯**。

9. 確認**部署衝突** 對話方塊隨即出現。

     會出現此對話方塊時 Visual Studio 嘗試部署方案 （清單執行個體），該方案已部署的 SharePoint 網站。 當您執行升級的部署步驟稍後在本逐步解說時，就不會出現此對話方塊。

10. 在 **部署衝突**對話方塊方塊中，選擇**自動解決**選項按鈕。

     Visual Studio 會刪除 SharePoint 網站上的清單執行個體，會部署在專案中，清單項目，然後開啟 SharePoint 網站。

11. 在 **列出**區段的 快速啟動 列中，選擇**員工**清單，並確認下列詳細資料：

    -   **附件**並**住家電話**資料行不會出現在這個檢視的清單。

    -   清單是空的。 當您使用**預設**要重新部署解決方案，部署組態**員工**清單取代專案中新的空白清單。

## <a name="test-the-deployment-step"></a>測試部署步驟
 您現在已準備好測試升級的部署步驟。 首先，在 SharePoint 中的清單執行個體中新增項目。 然後將變更的清單定義和清單執行個體中，將它們升級 SharePoint 網站，並確認升級的部署步驟不會覆寫新的項目。

#### <a name="to-manually-add-an-item-to-the-list"></a>若要以手動方式將項目加入清單

1.  SharePoint 網站，在功能區下方**清單工具**索引標籤上，選擇**項目** 索引標籤。

2.  在 **的新**群組中，選擇**新項目**。

     或者，您可以選擇**加入新項目**本身的項目清單中的連結。

3.  在 [**員工-新的項目**] 視窗，請在**標題**方塊中，輸入**設備經理**。

4.  在 **名字**方塊中，輸入**Andy**。

5.  在 **公司**方塊中，輸入**Contoso**。

6.  選擇**儲存**按鈕，確認新的項目出現在清單中，然後再關閉 web 瀏覽器。

     稍後在本逐步解說中，您將使用此項目，若要確認升級的部署步驟不會覆寫此清單的內容。

#### <a name="to-test-the-upgrade-deployment-step"></a>若要測試升級的部署步驟

1. 在 Visual Studio 中，實驗執行個體中**方案總管**，開啟捷徑功能表**EmployeesListDefinition**專案節點，然後選擇**屬性**.

    屬性編輯器/設計工具隨即開啟。

2. 在  **SharePoint**索引標籤上，設定**現用部署組態**屬性設**升級**。

    這項自訂部署設定包括新的升級部署步驟。

3. 開啟捷徑功能表**員工清單**項目時，專案，然後選擇**屬性**或是**開啟**。

    屬性編輯器/設計工具隨即開啟。

4. 上**檢視**索引標籤上，選擇**電子郵件**資料行，然後選擇**<** 將從該資料行的索引鍵**選取的資料行**清單**可用的資料行**清單。

    此動作會移除的預設檢視中的這些欄位**員工**SharePoint 網站上的清單。

5. 開始偵錯選擇**F5**金鑰或，功能表列選擇**偵錯** > **開始偵錯**。

6. 確認 Visual Studio 的其他執行個體中的程式碼是在您稍早在設定的中斷點上停止`CanExecute`方法。

7. 選擇**F5**重要的一次，或在功能表列上選擇 **偵錯** > **繼續**。

8. 請確認程式碼是在您稍早在設定的中斷點上停止`Execute`方法。

9. 選擇**F5**鍵，或在功能表列上選擇 **偵錯** > **繼續**最後一次。

     網頁瀏覽器會開啟 SharePoint 網站。

10. 在 **列出**區段的 快速啟動 區域中，選擇**員工**清單，並確認下列詳細資料：

    - 仍在清單中，是您稍早 （適用於 Andy，設備經理) 中手動加入的項目。

    - **公司電話**並**電子郵件地址**資料行不會出現在這個檢視的清單。

      **升級**部署組態可讓您修改現有**員工**SharePoint 網站上的清單執行個體。 如果您使用**預設**部署組態，而不是**升級**組態中，您會遇到部署衝突。 Visual Studio 會藉由取代來解決衝突**員工**清單和 Andy，設備管理員 中，項目不會刪除。

## <a name="clean-up-the-development-computer"></a>清除開發電腦
 完成測試升級的部署步驟之後，從 SharePoint 網站中，移除清單執行個體和清單定義，並移除 Visual Studio 中的部署步驟延伸模組。

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>若要從 SharePoint 網站中移除的清單執行個體

1.  開啟**員工**列出 SharePoint 網站上，如果清單尚未開啟。

2.  在功能區中的 SharePoint 網站上，選擇**清單工具**索引標籤，然後選擇**清單** 索引標籤。

3.  在 **設定**群組中，選擇**清單設定**項目。

4.  底下**權限與管理**，選擇**刪除這份清單**命令中，選擇 [**確定**以確認您要將清單傳送至資源回收筒]，然後關閉 web瀏覽器。

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>若要移除的 SharePoint 網站的清單定義

1.  在實驗性 Visual Studio 執行個體，在功能表列上，選擇**建置** > **Retract**。

     Visual Studio 會撤銷從 SharePoint 網站的清單定義。

#### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1.  在實驗性 Visual Studio 執行個體，在功能表列上，選擇**工具** > **擴充功能和更新**。

     [擴充功能和更新] 對話方塊隨即開啟。

2.  在延伸模組清單中，選擇**升級 SharePoint 專案的部署步驟**，然後選擇**解除安裝**命令。

3.  在出現的對話方塊中，選擇 **[是]** 以確認您想要解除安裝延伸模組，然後選擇**立即重新啟動**完成解除安裝。

4.  關閉 Visual Studio （實驗性執行個體和 UpgradeDeploymentStep 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
