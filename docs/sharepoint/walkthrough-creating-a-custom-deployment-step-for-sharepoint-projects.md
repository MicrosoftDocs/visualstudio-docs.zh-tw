---
title: "逐步解說： 建立 SharePoint 專案的自訂部署步驟 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 036f8d135e535547e9e5f790135186bf1f5728bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects"></a>逐步解說：建立 SharePoint 專案的自訂部署步驟
  當您部署 SharePoint 專案時，Visual Studio 會執行一系列的部署步驟，以特定順序。 Visual Studio 包含許多的內建部署步驟，但您也可以建立您自己。  
  
 在本逐步解說中，您將建立的自訂部署步驟，以升級執行 SharePoint 的伺服器上的方案。 Visual Studio 包含許多工作，這類撤銷或新增解決方案，內建部署步驟，但它不會包含如升級方案的部署步驟。 根據預設，當您部署 SharePoint 方案，Visual Studio 第一次會撤銷方案 （如果已部署），然後重新部署整個方案。 如需有關內建部署步驟的詳細資訊，請參閱[部署、 發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
 本逐步解說將示範下列工作：  
  
-   建立 Visual Studio 擴充功能會執行兩個主要工作：  
  
    -   延伸模組會定義要升級 SharePoint 方案的自訂部署步驟。  
  
    -   延伸模組建立定義新的部署組態，這是一組部署步驟，針對指定的專案中執行的專案擴充功能。 新的部署組態包括自訂部署步驟和數個內建部署步驟。  
  
-   建立兩個延伸模組組件呼叫的自訂 SharePoint 命令。 SharePoint 命令是使用伺服器物件模型中的應用程式開發介面 for SharePoint 的延伸模組組件可以呼叫的方法。 如需詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   建立要部署這兩個組件的 Visual Studio 擴充功能 (VSIX) 封裝。  
  
-   測試新的部署步驟。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說在開發電腦上：  
  
-   支援的 Windows、 SharePoint 和 Visual Studio 版本。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。 本逐步解說使用**VSIX 專案**建立 VSIX 封裝，來部署擴充功能 SDK 中的範本。 如需詳細資訊，請參閱[擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念是有幫助，但並非必要，完成此逐步解說：  
  
-   使用 for SharePoint 的伺服器物件模型。 如需詳細資訊，請參閱[使用 SharePoint Foundation 伺服器端物件模型](http://go.microsoft.com/fwlink/?LinkId=177796)。  
  
-   SharePoint 方案。 如需詳細資訊，請參閱[方案概觀](http://go.microsoft.com/fwlink/?LinkId=169422)。  
  
-   升級 SharePoint 方案。 如需詳細資訊，請參閱[升級方案](http://go.microsoft.com/fwlink/?LinkId=177802)。  
  
## <a name="creating-the-projects"></a>建立專案  
 若要完成此逐步解說，您必須建立三個專案：  
  
-   若要建立 VSIX 封裝，來部署擴充功能 VSIX 專案。  
  
-   類別庫專案，可實作延伸。 此專案必須以.NET Framework 4.5 為目標。  
  
-   類別庫專案來定義自訂 SharePoint 命令。 此專案必須以.NET Framework 3.5 為目標。  
  
 開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
3.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic**節點，然後選擇 **擴充性**節點。  
  
    > [!NOTE]  
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
4.  在對話方塊頂端，選擇  **.NET Framework 4.5**清單中的.NET Framework 版本。  
  
5.  選擇**VSIX 專案**範本，將專案**UpgradeDeploymentStep**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]新增**UpgradeDeploymentStep**專案加入**方案總管 中**。  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  在**方案總管] 中**，開啟 UpgradeDeploymentStep 方案節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic**節點，然後選擇  **Windows**節點。  
  
3.  在對話方塊頂端，選擇  **.NET Framework 4.5**清單中的.NET Framework 版本。  
  
4.  選擇**類別庫**專案範本，將專案命名**DeploymentStepExtension**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]新增**DeploymentStepExtension**專案加入方案，並開啟預設 Class1 的程式碼檔。  
  
5.  從專案刪除 Class1 的程式碼檔案。  
  
#### <a name="to-create-the-sharepoint-command-project"></a>若要建立 SharePoint 命令專案  
  
1.  在**方案總管] 中**，開啟 UpgradeDeploymentStep 方案節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic**，然後選擇  **Windows**節點。  
  
3.  在對話方塊頂端，選擇  **.NET Framework 3.5**清單中的.NET Framework 版本。  
  
4.  選擇**類別庫**專案範本，將專案命名**SharePointCommands**，然後選擇 [**確定**] 按鈕。  
  
     Visual Studio 會加入**SharePointCommands**專案加入方案，並開啟預設 Class1 的程式碼檔。  
  
5.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configuring-the-projects"></a>設定專案  
 您撰寫程式碼來建立自訂部署步驟之前，您必須加入程式碼檔案和組件參考，而且您必須設定專案。  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>若要設定 DeploymentStepExtension 專案  
  
1.  在**DeploymentStepExtension**專案中，加入兩個具有下列名稱的程式碼檔案：  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  開啟於 DeploymentStepExtension 專案，並在專案的捷徑功能表，然後選擇**加入參考**。  
  
3.  在**Framework**索引標籤上，選取核取方塊，針對 System.ComponentModel.Composition 組件。  
  
4.  在**延伸**索引標籤上，對於 Microsoft.VisualStudio.SharePoint 組件中，選取核取方塊，然後選擇**確定** 按鈕。  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>若要設定 SharePointCommands 專案  
  
1.  在**SharePointCommands**專案中，加入名為命令的程式碼檔案。  
  
2.  在**方案總管 中**，開啟捷徑功能表上**SharePointCommands**專案節點，然後選擇**加入參考**。  
  
3.  在**延伸**索引標籤上的下列組件中，選取核取方塊，然後按一下 選擇**確定**按鈕  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="defining-the-custom-deployment-step"></a>定義自訂部署步驟  
 建立一個類別來定義升級部署步驟。 若要定義部署步驟，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>介面。 每當您想要定義的自訂部署步驟，請實作這個介面。  
  
#### <a name="to-define-the-custom-deployment-step"></a>若要定義自訂部署步驟  
  
1.  在**DeploymentStepExtension**專案中，開啟 UpgradeStep 程式碼檔案，並接著將下列程式碼貼入其中。  
  
    > [!NOTE]  
    >  加入下列程式碼，專案就會發生編譯錯誤，但它們會消失之後當您加入程式碼在稍後步驟中。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="creating-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>建立部署組態，包括自訂部署步驟  
 建立新的部署組態，其中包括數個內建部署步驟和新的升級部署步驟專案擴充功能。 藉由建立此擴充功能，您可以協助使用升級的部署步驟，在 SharePoint 專案中的 SharePoint 開發人員。  
  
 若要建立的部署組態，該類別會實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>介面。 每當您想要建立 SharePoint 專案擴充功能時，請實作這個介面。  
  
#### <a name="to-create-the-deployment-configuration"></a>若要建立的部署組態  
  
1.  
  
2.  在**DeploymentStepExtension**專案中，開啟 DeploymentConfigurationExtension 程式碼檔案，並接著將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>建立自訂 SharePoint 命令  
 建立兩個 sharepoint 伺服器物件模型呼叫的自訂命令。 一個命令會判斷是否已部署方案。另一個命令會升級方案。  
  
#### <a name="to-define-the-sharepoint-commands"></a>若要定義 SharePoint 命令  
  
1.  在**SharePointCommands**專案中，開啟指令碼檔案，並接著將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>檢查點  
 此時在逐步解說中，自訂部署步驟和 SharePoint 命令的所有程式碼現在都會是專案。 建置，以確保它們編譯無誤。  
  
#### <a name="to-build-the-projects"></a>若要建置的專案  
  
1.  在**方案總管 中**，開啟捷徑功能表**DeploymentStepExtension**專案，然後再選擇**建置**。  
  
2.  開啟快顯功能表**SharePointCommands**專案，然後再選擇**建置**。  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 封裝，來部署擴充功能  
 若要部署擴充功能，方案中使用 VSIX 專案建立 VSIX 封裝。 首先，設定 VSIX 封裝，藉由修改 source.extension.vsixmanifest 檔案中的，在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要設定，並建立 VSIX 封裝  
  
1.  在**方案總管] 中**下**UpgradeDeploymentStep**專案中，開啟捷徑功能表**source.extension.vsixmanifest**檔案，然後再選擇 [ **開啟**。  
  
     Visual Studio 會在資訊清單編輯器中開啟檔案。 Source.extension.vsixmanifest 檔案是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱[VSIX 擴充功能結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**產品名稱**方塊中，輸入**升級 SharePoint 專案的部署步驟**。  
  
3.  在**作者**方塊中，輸入**Contoso**。  
  
4.  在**描述**方塊中，輸入**提供可以在 SharePoint 專案中使用的自訂升級的部署步驟**。  
  
5.  在**資產** 索引標籤的編輯器中，選擇 **新增** 按鈕。  
  
     **加入新資產** 對話方塊隨即出現。  
  
6.  在**類型**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個項目 VSIX 封裝中指定延伸模組組件的名稱。 如需詳細資訊，請參閱[MEFComponent 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**來源**清單中，選擇**目前方案中的專案**。  
  
8.  在**專案**清單中，選擇**DeploymentStepExtension**，然後選擇 [**確定**] 按鈕。  
  
9. 在資訊清單編輯器中，選擇 **新增**按鈕一次。  
  
     **加入新資產** 對話方塊隨即出現。  
  
10. 在**類型**清單中，輸入**SharePoint.Commands.v4**。  
  
    > [!NOTE]  
    >  這個項目會指定您想要包含在 Visual Studio 擴充功能的自訂延伸模組。 如需詳細資訊，請參閱[資產項目 （VSX 結構描述）](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
11. 在**來源**清單中，選擇**目前方案中的專案**。  
  
12. 在**專案**清單中，選擇**SharePointCommands**，然後選擇 [**確定**] 按鈕。  
  
13. 在功能表列上選擇 **建置**，**建置方案**，然後確認方案編譯無誤。  
  
14. 請確定 UpgradeDeploymentStep 專案建置輸出資料夾現在包含 UpgradeDeploymentStep.vsix 檔案。  
  
     根據預設，會將組建輸出資料夾...包含專案檔的資料夾下的 \bin\Debug 資料夾。  
  
## <a name="preparing-to-test-the-upgrade-deployment-step"></a>準備要測試升級的部署步驟  
 若要測試升級的部署步驟，您必須先在 SharePoint 網站部署範例方案。 開始偵錯 Visual Studio 的實驗執行個體中的擴充功能。 接著建立清單定義和清單執行個體，用來測試部署步驟，並再將其部署至 SharePoint 網站。 接下來，修改的清單定義和清單執行個體，然後重新部署，示範如何在預設部署程序會覆寫 SharePoint 網站上的方案。  
  
 稍後在本逐步解說中，您將修改的清單定義和清單執行個體，然後您會升級它們，然後在 SharePoint 網站上。  
  
#### <a name="to-start-debugging-the-extension"></a>若要啟動偵錯擴充功能  
  
1.  系統管理認證，以重新啟動 Visual Studio，然後開啟 UpgradeDeploymentStep 方案。  
  
2.  在 DeploymentStepExtension 專案中，開啟 UpgradeStep 程式碼檔案，並再將中斷點加入至程式碼中的第一行`CanExecute`和`Execute`方法。  
  
3.  開始偵錯方法選擇 F5 鍵，或是在功能表列上，選擇**偵錯**，**開始偵錯**。  
  
4.  Visual Studio 會擴充功能安裝 SharePoint Projects\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 部署步驟，並啟動 Visual studio 的實驗執行個體。 您將這個執行個體的 Visual Studio 中測試升級的部署步驟。  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>若要建立 SharePoint 專案使用清單定義和清單執行個體  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**檔案**，**新增**，**專案**。  
  
2.  在**新的專案**對話方塊方塊中，展開 [ **Visual C#**節點或**Visual Basic** ] 節點，展開**SharePoint** ] 節點，然後選擇 [**2010年**節點。  
  
3.  在對話方塊頂端，請確定**.NET Framework 3.5**會出現在.NET Framework 版本的清單。  
  
     專案[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]需要這個版本的.NET Framework。  
  
4.  在專案範本清單中選擇**SharePoint 2010 專案**，將專案命名**EmployeesListDefinition**，然後選擇 [ **[確定]** ] 按鈕。  
  
5.  在**SharePoint 自訂精靈**，輸入您想要用於偵錯的網站 URL。  
  
6.  在下**此 SharePoint 方案的信任層級為何**，選擇**部署為伺服陣列方案**選項按鈕。  
  
    > [!NOTE]  
    >  升級部署步驟並不支援沙箱化方案。  
  
7.  選擇**完成** 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]建立 EmployeesListDefinition 專案。  
  
8.  開啟 EmployeesListDefinition 專案的捷徑功能表，選擇 **新增**，然後選擇 **新項目**。  
  
9. 在**加入新項目-EmployeesListDefinition**對話方塊方塊中，展開  **SharePoint**  節點，然後選擇  **2010年**節點。  
  
10. 選擇**清單**項目範本，將項**員工清單**，然後選擇 [**新增**] 按鈕。  
  
     SharePoint 自訂精靈 隨即出現  
  
11. 在**選擇清單設定**頁面上，確認下列設定，然後選擇 **完成**按鈕：  
  
    1.  **員工清單**會出現在**您想要清單顯示什麼名稱？**方塊。  
  
    2.  **建立自訂的清單為基礎：**會選擇選項按鈕。  
  
    3.  **預設值 （空白）**中選擇**建立自訂的清單為基礎：**清單。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]建立員工清單項目的標題欄與單一的空執行個體，並開啟清單設計工具。  
  
12. 在清單設計工具上**資料行**索引標籤上，選擇**輸入新的或現有的資料行名稱**資料列，然後再加入下列資料行中的**資料行的顯示名稱**清單：  
  
    1.  名字  
  
    2.  公司  
  
    3.  公司電話  
  
    4.  電子郵件  
  
13. 儲存所有檔案，然後再關閉 清單設計工具。  
  
14. 在**方案總管 中**，依序展開**員工清單** 節點，然後展開**員工清單執行個體**子節點。  
  
15. 在 Elements.xml 檔案中，取代預設的 XML 檔案中以下列 XML。 這段 XML 會變更的清單名稱**員工**，並將具有名為 Jim 宗翰的員工的資訊。  
  
    ```  
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
  
16. 儲存並關閉 Elements.xml 檔案。  
  
17. 開啟 EmployeesListDefinition 專案的捷徑功能表，然後選擇**開啟**或**屬性**。  
  
     屬性設計工具隨即開啟。  
  
18. 在**SharePoint**索引標籤上，清除**偵錯後自動撤銷**核取方塊，然後再儲存屬性。  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>若要部署的清單定義和清單執行個體  
  
1.  在**方案總管 中**，選擇**EmployeesListDefinition**專案節點。  
  
2.  在**屬性**視窗中，請確定**現用部署組態**屬性設定為**預設**。  
  
3.  選擇 F5 鍵，或在功能表列上選擇 **偵錯**，**開始偵錯**。  
  
4.  確認專案建置成功，網頁瀏覽器會開啟 SharePoint 網站，**列出**快速啟動 列中的項目中包括新**員工** 清單中，而且**員工**Jim 宗翰清單包含項目。  
  
5.  關閉網頁瀏覽器。  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>若要修改的清單定義和清單執行個體，並將其重新佈署  
  
1.  在 EmployeesListDefinition 專案中，開啟 子系的 Elements.xml 檔案**員工清單執行個體**專案項目。  
  
2.  移除`Data`元素和其子系的 Jim 宗翰移除項目，從清單中。  
  
     當您完成時，此檔案應該包含下列 XML。  
  
    ```  
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
  
3.  儲存並關閉 Elements.xml 檔案。  
  
4.  開啟快顯功能表**員工清單**項目、 專案，然後選擇**開啟**或**屬性**。  
  
5.  在清單設計工具中，選擇 [**檢視**] 索引標籤。  
  
6.  在**選取的資料行**清單中，選擇**附件**，然後選擇 < 鍵以移至該資料行**可用的資料行**清單。  
  
7.  重複上述步驟來移動**公司電話**資料行從**選取的資料行**清單**可用的資料行**清單。  
  
     這個動作會移除這些欄位的預設檢視從**員工**SharePoint 網站上的清單。  
  
8.  開始偵錯方法選擇 F5 鍵，或是在功能表列上，選擇**偵錯**，**開始偵錯**。  
  
9. 確認**部署衝突** 對話方塊隨即出現。  
  
     這個對話方塊就會出現 Visual Studio 嘗試部署方案 （清單執行個體） 的方案已經部署在 SharePoint 網站。 當您執行升級的部署步驟稍後在本逐步解說中，不會出現此對話方塊。  
  
10. 在**部署衝突**對話方塊方塊中，選擇**自動解決**選項按鈕。  
  
     Visual Studio 刪除 SharePoint 網站上的清單執行個體、 將部署在專案中，清單項目，然後開啟 SharePoint 網站。  
  
11. 在**列出**區段的 快速啟動 列中，選擇 **員工**清單，並確認下列詳細資料：  
  
    -   **附件**和**住家電話**資料行不會出現在這個檢視的清單。  
  
    -   清單是空的。 當您使用**預設**重新部署方案的部署組態**員工**清單取代您的專案中的新空白清單。  
  
## <a name="testing-the-deployment-step"></a>測試部署步驟  
 現在您已經準備好進行測試升級的部署步驟。 首先，在 SharePoint 中的清單執行個體中加入項目。 然後變更 清單定義和清單執行個體中，將它們升級 SharePoint 網站，並確認升級部署步驟，不會覆寫新增的項目。  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>若要以手動方式將項目加入清單  
  
1.  在功能區中，於 SharePoint 網站上底下**清單工具**索引標籤上，選擇**項目** 索引標籤。  
  
2.  在**新增**群組中，選擇**新項目**。  
  
     或者，您可以選擇**加入新項目**本身的項目清單中的連結。  
  
3.  在**員工-新項目**視窗，請在**標題**方塊中，輸入**設備經理**。  
  
4.  在**名字**方塊中，輸入**Andy**。  
  
5.  在**公司**方塊中，輸入**Contoso**。  
  
6.  選擇**儲存**按鈕，確認新的項目出現在清單中，然後再關閉網頁瀏覽器。  
  
     稍後在本逐步解說中，您將使用此項目，若要確認升級的部署步驟，不會覆寫此清單的內容。  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>若要測試升級的部署步驟  
  
1.  在 Visual Studio 的實驗執行個體中**方案總管 中**，開啟捷徑功能表**EmployeesListDefinition**專案節點，然後選擇**屬性**.  
  
     屬性編輯器/設計工具隨即開啟。  
  
2.  在**SharePoint**索引標籤上，設定**現用部署組態**屬性**升級**。  
  
     這項自訂部署設定包括新的升級部署步驟。  
  
3.  開啟快顯功能表**員工清單**項目、 專案，然後選擇**屬性**或**開啟**。  
  
     屬性編輯器/設計工具隨即開啟。  
  
4.  上**檢視**索引標籤上，選擇**電子郵件**資料行，然後選擇   **<** 移動從該資料行的索引鍵**選取的資料行**清單**可用的資料行**清單。  
  
     這個動作會移除這些欄位的預設檢視從**員工**SharePoint 網站上的清單。  
  
5.  開始偵錯方法選擇 F5 鍵，或是在功能表列上，選擇**偵錯**，**開始偵錯**。  
  
6.  確認 Visual Studio 的其他執行個體中的程式碼是您稍早在設定的中斷點上停止`CanExecute`方法。  
  
7.  再次選擇 F5 鍵，或在功能表列上選擇 **偵錯**，**繼續**。  
  
8.  請確認程式碼是您稍早在設定的中斷點上停止`Execute`方法。  
  
9. 選擇 F5 鍵，或在功能表列上選擇 **偵錯**，**繼續**最後一次。  
  
     網頁瀏覽器會開啟 SharePoint 網站。  
  
10. 在**列出**區段的 快速啟動 區域中，選擇 **員工**清單，並確認下列詳細資料：  
  
    -   您稍早 （針對 Andy 設備經理) 中以手動方式加入的項目是仍在清單中。  
  
    -   **公司電話**和**電子郵件地址**資料行不會出現在這個檢視的清單。  
  
     **升級**部署組態可讓您修改現有**員工**SharePoint 網站上的清單執行個體。 如果您使用**預設**部署組態，而不是**升級**組態中，您會遇到部署衝突。 Visual Studio 會解決此衝突，取代**員工** 清單中，與 Andy，設備管理員 中，項目，就會刪除。  
  
## <a name="cleaning-up-the-development-computer"></a>清除開發電腦  
 完成測試升級的部署步驟之後，從 SharePoint 網站中，移除清單執行個體和清單定義，並移除 Visual Studio 中的部署步驟延伸模組。  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>若要移除的清單執行個體從 SharePoint 網站  
  
1.  開啟**員工**列出 SharePoint 網站上，如果還沒有開啟的清單。  
  
2.  在功能區中的 SharePoint 網站上，選擇 **清單工具**索引標籤，然後選擇 **清單** 索引標籤。  
  
3.  在**設定**群組中，選擇**清單設定**項目。  
  
4.  下**權限與管理**，選擇**刪除這份清單**命令中，選擇**確定**來確認您要將清單傳送至資源回收筒，然後關閉 web瀏覽器。  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>若要從 SharePoint 網站移除清單定義  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**建置**， **Retract**。  
  
     Visual Studio 會撤銷從 SharePoint 網站的清單定義。  
  
#### <a name="to-uninstall-the-extension"></a>安裝擴充功能  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**工具**，**擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在 擴充功能的清單中，選擇 **升級 SharePoint 專案的部署步驟**，然後選擇 **解除安裝**命令。  
  
3.  在出現的對話方塊中，選擇 **是**來確認您要解除安裝擴充功能，然後選擇 **立即重新啟動**完成解除安裝。  
  
4.  關閉 Visual Studio （實驗性執行個體和 UpgradeDeploymentStep 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。  
  
## <a name="see-also"></a>請參閱  
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  