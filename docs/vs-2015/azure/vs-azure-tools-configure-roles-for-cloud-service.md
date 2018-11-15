---
title: 使用 Visual Studio 設定 Azure 雲端服務的角色 |Microsoft Docs
description: 了解如何安裝及設定使用 Visual Studio 的 Azure 雲端服務的角色。
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ce2259debb55c4792c2998f0e67df69dbc8cb7f9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002088"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>使用 Visual Studio 來設定 Azure 雲端服務角色
Azure 雲端服務可以有一或多個背景工作角色或 web 角色。 針對每個角色，您需要定義該角色的設定方式，也可以設定該角色的執行方式。 若要深入了解雲端服務中的角色，請參閱視訊[Introduction to Azure 雲端服務](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services)。 

您的雲端服務的資訊儲存在下列檔案：

- **ServiceDefinition.csdef** -服務定義檔定義您的雲端服務，包括需要哪些角色、 端點和虛擬機器大小的執行階段設定。 不會儲存在資料`ServiceDefinition.csdef`您的角色執行時，可以變更。
- **ServiceConfiguration.cscfg** -服務組態檔可讓您設定執行的角色執行個體數目，並為角色定義的設定值。 中儲存的資料`ServiceConfiguration.cscfg`您的角色執行時，可以變更。

若要儲存不同的值，控制角色的執行方式的設定，您可以定義多個服務組態。 您可以針對每個部署環境使用不同的服務。 例如，您可以設定您的儲存體帳戶連接字串，以使用本機 Azure 儲存體模擬器在本機服務組態，並建立使用 Azure 儲存體在雲端中的另一個服務組態。

當您在 Visual Studio 中建立 Azure 雲端服務時，兩個服務組態會自動建立，並新增至您的 Azure 專案：

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>設定 Azure 雲端服務
下列步驟所示，您可以在 Visual Studio 中，設定 Azure 雲端服務從方案總管 中：

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 **方案總管**，以滑鼠右鍵按一下專案，並從操作功能表中，選取**屬性**。
   
    ![方案總管專案操作功能表](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. 在專案的屬性頁面中，選取**開發** 索引標籤。 

    ![專案內容頁面-開發索引標籤](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. 在 **服務組態**清單中，選取您想要編輯服務組態的名稱。 (如果您想要變更此角色的所有服務組態，請選取**所有組態**。)
   
    > [!IMPORTANT]
    > 如果您選擇特定服務組態，因為它們僅針對所有組態設定，會停用某些屬性。 若要編輯這些屬性，您必須選取**所有組態**。
    > 
    > 
   
    ![Azure 雲端服務的服務組態清單](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>變更角色執行個體數目
若要改善您的雲端服務的效能，您可以變更角色的執行，根據使用者數目或特定角色的預期負載的執行個體數目。 個別的虛擬機器的每個角色執行個體執行時所建立的雲端服務在 Azure 中。 這會影響這個雲端服務的部署計費。 如需有關計費的詳細資訊，請參閱[了解 Microsoft Azure 帳單](/azure/billing/billing-understand-your-bill)。

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 [**方案總管] 中**，展開專案節點。 底下**角色**節點，以滑鼠右鍵按一下您想要更新，並從操作功能表中，選取 的角色**屬性**。

    ![方案總管 Azure 角色操作功能表](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選取 [**組態**] 索引標籤。

    ![設定 索引標籤](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. 在 **服務組態**清單中，選取您想要更新的服務組態。
   
    ![服務組態清單](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. 在 **執行個體計數**文字中，輸入您要啟動此角色的執行個體數目。 個別的虛擬機器上的事件，是當您發行至 Azure 的雲端服務時執行的每個執行個體。

    ![更新執行個體計數](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. 從 Visual Studio 中的工具列上，選取**儲存**。

## <a name="manage-connection-strings-for-storage-accounts"></a>管理儲存體帳戶的連接字串
您可以新增、 移除或修改服務組態的連接字串。 例如，您可以本機連接字串，其值為本機服務組態`UseDevelopmentStorage=true`。 您也可以設定雲端服務組態在 Azure 中使用的儲存體帳戶。

> [!WARNING]
> 當您輸入 Azure 儲存體帳戶金鑰資訊，儲存體帳戶連接字串時，這項資訊儲存在本機服務組態檔中。 不過，這項資訊是目前不會儲存為加密的文字。
> 
> 

藉由使用不同的值，每個服務組態，您不必在您的雲端服務中使用不同的連接字串，或您的雲端服務發行至 Azure 時修改程式碼。 您可以在程式碼中使用的連接字串的相同名稱和值都不同，根據您選取當您建置您的雲端服務或發佈該服務組態。

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 [**方案總管] 中**，展開專案節點。 底下**角色**節點，以滑鼠右鍵按一下您想要更新，並從操作功能表中，選取 的角色**屬性**。

    ![方案總管 Azure 角色操作功能表](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選取 [**設定**] 索引標籤。

    ![設定 索引標籤](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. 在 **服務組態**清單中，選取您想要更新的服務組態。

    ![服務組態](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. 若要新增連接字串，請選取**新增設定**。

    ![新增連接字串](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. 一旦新的設定已加入至清單，更新所需的資訊清單中的資料列。

    ![新的連接字串](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **名稱**-輸入您想要使用的連接字串的名稱。
    - **型別**-選取**連接字串**從下拉式清單。
    - **值**-您可以輸入連接字串直接**值**儲存格中，或選取省略符號 （...），以用於**建立的儲存體連接字串**對話方塊。  

1. 在 [**建立儲存體連接字串**] 對話方塊中，選取一個選項，如**連線使用**。 然後遵循您所選取的選項：

    - **Microsoft Azure 儲存體模擬器**-如果您選取此選項時，對話方塊上的其餘設定會停用，因為它們只適用於 Azure。 選取 [確定]。
    - **您的訂用帳戶**-如果您選取此選項時，使用下拉式清單中選取，然後登入 Microsoft 帳戶，或新增 Microsoft 帳戶。 選取 Azure 訂用帳戶和儲存體帳戶。 選取 [確定]。
    - **手動輸入的認證**-輸入儲存體帳戶名稱和主要或次要金鑰。 選取的選項**連線**（HTTPS 建議大部分的情況下）。選取 [確定]。

1. 若要刪除的連接字串，選取 連接字串，然後按**移除設定**。

1. 從 Visual Studio 中的工具列上，選取**儲存**。

## <a name="programmatically-access-a-connection-string"></a>以程式設計方式存取連接字串

下列步驟示範如何以程式設計方式存取連接字串使用C#。

1. 新增下列 using 指示詞至C#您要使用設定的檔案：

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. 下列程式碼說明如何存取連接字串的範例。 取代&lt;ConnectionStringName > 預留位置取代為適當的值。 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>新增要在 Azure 雲端服務中使用自訂設定
服務組態檔中的自訂設定可讓您新增名稱和特定服務組態的字串值。 您可以選擇使用此設定來設定雲端服務中的某項功能，藉由讀取設定的值，並使用此值來控制您的程式碼中的邏輯。 您可以變更這些服務組態值，而不需要重建服務封裝或執行您的雲端服務時。 設定變更時，您的程式碼可以檢查的通知。 請參閱[RoleEnvironment.Changing 事件](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx)。

您可以新增、 移除或修改服務組態的自訂設定。 您可能想要顯示這些字串的不同服務組態不同的值。

藉由使用不同的值，每個服務組態，您不必在您的雲端服務中使用不同的字串，或您的雲端服務發行至 Azure 時修改程式碼。 您可以在程式碼中使用相同名稱的字串，並為不同的值，根據您選取當您建置您的雲端服務或發佈該服務組態。

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 [**方案總管] 中**，展開專案節點。 底下**角色**節點，以滑鼠右鍵按一下您想要更新，並從操作功能表中，選取 的角色**屬性**。

    ![方案總管 Azure 角色操作功能表](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選取 [**設定**] 索引標籤。

    ![設定 索引標籤](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. 在 **服務組態**清單中，選取您想要更新的服務組態。

    ![服務組態清單](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. 若要新增自訂設定，請選取**新增設定**。

    ![新增自訂設定](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. 一旦新的設定已加入至清單，更新所需的資訊清單中的資料列。

    ![新的自訂設定](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **名稱**-輸入設定的名稱。
    - **型別**-選取**字串**從下拉式清單。
    - **值**-輸入設定的值。 您可以輸入的值直接**值**儲存格中，或選取省略符號 （...），以輸入的值中**編輯字串**對話方塊。  

1. 若要刪除自訂的設定，請選取設定，然後按**移除設定**。

1. 從 Visual Studio 中的工具列上，選取**儲存**。

## <a name="programmatically-access-a-custom-settings-value"></a>以程式設計方式存取自訂設定的值
 
下列步驟示範如何以程式設計方式存取 自訂設定，使用C#。

1. 新增下列 using 指示詞至C#您要使用設定的檔案：

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. 下列程式碼說明如何存取自訂設定的範例。 取代&lt;SettingName > 預留位置取代為適當的值。 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>管理每個角色執行個體的本機儲存體
您可以新增每個角色執行個體的本機檔案系統儲存體。 儲存在該儲存體不存取之角色的資料儲存的其他執行個體或其他角色的資料。  

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 [**方案總管] 中**，展開專案節點。 底下**角色**節點，以滑鼠右鍵按一下您想要更新，並從操作功能表中，選取 的角色**屬性**。

    ![方案總管 Azure 角色操作功能表](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選取 [**本機儲存體**] 索引標籤。

    ![本機儲存體 索引標籤](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. 在 **服務組態**清單中，請確認**所有組態**已選取本機儲存體設定會套用至所有服務組態。 [已停用] 頁面上的所有輸入欄位會產生任何其他值。 

    ![服務組態清單](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. 若要新增的本機儲存體項目，請選取**新增本機儲存體**。

    ![新增本機儲存體](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. 一旦新的本機儲存體項目加入至清單，更新所需的資訊清單中的資料列。

    ![新的本機儲存體項目](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **名稱**-輸入您想要用於新的本機儲存體的名稱。
    - **大小 (MB)** -輸入新的本機儲存體所需的 MB 大小。
    - **清除於角色回收**-選取這個選項，虛擬機器角色回收時，新的本機儲存體中移除資料。

1. 若要刪除本機儲存體項目，選取項目，然後按**移除本機儲存體**。

1. 從 Visual Studio 中的工具列上，選取**儲存**。

## <a name="programmatically-accessing-local-storage"></a>以程式設計方式存取本機儲存體

本章節將說明如何以程式設計方式存取 本機儲存體使用C#藉由撰寫測試文字檔案`MyLocalStorageTest.txt`。  

### <a name="write-a-text-file-to-local-storage"></a>文字檔案寫入本機儲存體

下列程式碼示範如何將文字檔案寫入本機儲存體。 取代&lt;Localstoragename> > 預留位置取代為適當的值。 

    ```csharp
    // Retrieve an object that points to the local storage resource
    LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");
    
    //Define the file name and path
    string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
    String filePath = Path.Combine(paths);
    
    using (FileStream writeStream = File.Create(filePath))
    {
        Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
        writeStream.Write(textToWrite, 0, textToWrite.Length);
    }

    ```

### <a name="find-a-file-written-to-local-storage"></a>尋找檔案寫入本機儲存體

若要檢視上一節中的程式碼所建立的檔案，請遵循下列步驟：
    
1.  在 Windows 通知區域中，以滑鼠右鍵按一下 Azure 圖示，並從操作功能表中，選取**顯示計算模擬器 UI**。 

    ![顯示 Azure 計算模擬器](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. 選取 web 角色。

    ![Azure 計算模擬器](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. 在  **Microsoft Azure 計算模擬器**功能表上，選取**工具** > **開啟本機存放區**。

    ![開啟本機存放區功能表項目](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. [Windows 檔案總管] 視窗開啟時，輸入 'MyLocalStorageTest.txt' 到**搜尋**文字方塊中，然後選取**Enter**開始搜尋。 

## <a name="next-steps"></a>後續步驟
深入了解 Visual Studio 中的 Azure 專案，請閱讀[設定 Azure 專案](vs-azure-tools-configuring-an-azure-project.md)。 深入了解雲端服務結構描述，請閱讀[結構描述參考](https://msdn.microsoft.com/library/azure/dd179398)。

