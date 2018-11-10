---
title: Azure DevOps 服務使用 Azure 資源群組專案中的連續整合 |Microsoft Docs
description: 描述如何使用 Azure 資源群組部署專案在 Visual Studio 中設定 Azure DevOps 服務中的持續整合。
author: mlearned
manager: douge
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: f6404b15e8a7cd3f95ac63bbae6076ef62fcff06
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002046"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Azure DevOps 服務使用 Azure 資源群組部署專案中的持續整合
若要部署 Azure 範本，您必須執行工作中各個階段： 組建、 測試、 複製到 Azure （也稱為 「 暫存 」） 及部署範本。 有兩種不同的方式，將範本部署到 Azure 的 DevOps 服務。 這兩種方法提供相同的結果，因此請選擇最適合您的工作流程。

1. 包含在 Azure 資源群組部署專案 (Deploy-AzureResourceGroup.ps1) 中的 PowerShell 指令碼會執行您組建管線中新增一個步驟。 指令碼會複製構件，並接著部署範本。
2. 新增多個 Azure DevOps 服務建置步驟，每個執行階段工作。

這篇文章會示範這兩個選項。 第一個選項的優點是能夠使用相同的指令碼由 Visual Studio 中的開發人員和整個生命週期中的提供一致性。 第二個選項可提供內建的指令碼的方便替代。 這兩個程序假設您已經有 Visual Studio 部署專案簽入至 Azure 的 DevOps 服務。

## <a name="copy-artifacts-to-azure"></a>將構件複製到 Azure
不論此案例中，如果您有任何需要進行範本部署的構件您必須提供 Azure Resource Manager 存取權。 這些成品可以包括下列檔案：

* 巢狀的範本
* 設定指令碼及 DSC 指令碼
* 應用程式二進位檔

### <a name="nested-templates-and-configuration-scripts"></a>巢狀的範本和設定指令碼
當您使用 Visual Studio 所提供的範本 （或使用 Visual Studio 程式碼片段建置） 的 PowerShell 指令碼不僅會暫存構件，它也會參數化不同的部署資源的 URI。 指令碼將構件複製到安全的容器，在 Azure 中、 建立的 SaS 權杖，該容器中，然後再傳遞至範本部署該資訊。 請參閱[建立範本部署](https://msdn.microsoft.com/library/azure/dn790564.aspx)若要深入了解巢狀範本。  當使用 Azure DevOps 服務中的工作，您必須針對範本部署選取適當的工作，並如有需要，從預備步驟傳遞參數值至範本部署。

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>設定 Azure 管線中的持續部署
若要在 Azure 的管線中呼叫 PowerShell 指令碼，您需要更新您組建管線。 簡單地說，步驟如下： 

1. 編輯組建管線。
2. 設定 Azure 管線中的 Azure 授權。
3. 新增參考 Azure 資源群組部署專案中的 PowerShell 指令碼的 Azure PowerShell 建置步驟。
4. 設定的值 *-ArtifactsStagingDirectory*才能在 Azure 中的管線所建置的專案使用的參數。

### <a name="detailed-walkthrough-for-option-1"></a>選項 1 的詳細逐步解說
下列程序會引導您在 Azure DevOps 服務使用的單一工作，在您的專案中執行 PowerShell 指令碼中設定連續部署所需的步驟。 

1. 編輯您的 Azure DevOps 服務建置管線，並新增 Azure PowerShell 建置步驟。 選擇組建管線底下**建置管線**類別目錄，然後選擇**編輯**連結。
   
   ![編輯組建管線][0]
2. 加入新**Azure PowerShell**組建至組建管線的步驟，然後選擇 **新增建置步驟...** 按鈕。
   
   ![加入建置步驟][1]
3. 選擇**部署工作**類別目錄中，選取**Azure PowerShell**工作，並再選擇其**新增** 按鈕。
   
   ![新增工作][2]
4. 選擇**Azure PowerShell**組建步驟，然後填入其值。
   
   1. 如果您已經有 Azure 服務端點新增至 Azure 的 DevOps 服務，選擇訂用帳戶**Azure 訂用帳戶**下拉式清單方塊並跳至下一節。 
      
      如果您沒有 Azure DevOps 服務中將 Azure 服務端點，您需要新增一個。 本小節會帶領您完成此程序。 如果您的 Azure 帳戶使用 Microsoft 帳戶 （例如 Hotmail)，您必須採取下列步驟，以取得服務主體驗證。

   2. 選擇**管理**連結**Azure 訂用帳戶**下拉式清單方塊。
      
      ![管理 Azure 訂用帳戶][3]
   3. 選擇**Azure**中**新的服務端點**下拉式清單方塊。
      
      ![新的服務端點][4]
   4. 在 **新增 Azure 訂用帳戶**對話方塊中，選取**服務主體**選項。
      
      ![服務主體選項][5]
   5. 將您的 Azure 訂用帳戶資訊加入**新增 Azure 訂用帳戶** 對話方塊。 您必須提供下列項目：
      
      * 訂用帳戶識別碼
      * 訂用帳戶名稱
      * 服務主體識別碼
      * 服務主體金鑰
      * 租用戶識別碼
   6. 將您選擇的名稱加入**訂用帳戶**名稱 方塊中。 此值稍後會出現**Azure 訂用帳戶**Azure DevOps 服務中的下拉式清單。 

   7. 如果您不知道您的 Azure 訂用帳戶識別碼，您可以使用下列命令來擷取它。
      
      如需 PowerShell 指令碼，請使用：
      
      `Get-AzureRmSubscription`
      
      針對 Azure CLI，請使用：
      
      `azure account show`
   8. 若要取得的服務主體識別碼、 服務主體金鑰及租用戶識別碼，後續的程序[建立 Active Directory 應用程式和服務主體使用入口網站](/azure/azure-resource-manager/resource-group-create-service-principal-portal)或[驗證與 Azure 服務主體Resource Manager](/azure/azure-resource-manager/resource-group-authenticate-service-principal)。
   9. 新增服務主體識別碼、 服務主體金鑰及租用戶識別碼的值，以**新增 Azure 訂用帳戶**對話方塊方塊，然後選擇**確定** 按鈕。
      
      現在，您會有有效的服務主體，要用來執行 Azure PowerShell 指令碼。
5. 編輯建置管線，然後選擇**Azure PowerShell**建置步驟。 選取之訂用帳戶**Azure 訂用帳戶**下拉式清單方塊。 (如果訂用帳戶未出現，請選擇**重新整理**按鈕旁**管理**連結。) 
   
   ![設定 Azure PowerShell 建置工作][8]
6. 提供 Deploy-AzureResourceGroup.ps1 PowerShell 指令碼的路徑。 若要這樣做，請選擇省略符號 （...） 按鈕旁**指令碼路徑**方塊中，瀏覽至中的 Deploy-AzureResourceGroup.ps1 PowerShell 指令碼**指令碼**資料夾的專案中，選取它，然後選擇**確定** 按鈕。    
   
   ![選取要編寫指令碼的路徑][9]
7. 選取的指令碼之後，更新路徑的指令碼以便從 Build.StagingDirectory 執行 (相同的目錄， *ArtifactsLocation*設)。 您可以加上"$(Build.stagingdirectory 「 若要在指令碼路徑的開頭。
   
    ![編輯指令碼路徑][10]
8. 在 **指令碼引數**方塊中，輸入下列參數 （在同一行）。 當您在 Visual Studio 中執行指令碼時，您可以看到 VS 如何使用中的參數**輸出**視窗。 您可以做為起點使用此建置步驟中設定的參數值。
   
   | 參數 | 描述 |
   | --- | --- |
   | -ResourceGroupLocation |資源群組所在位置，例如地理位置值**eastus**或是 **「 美國東部 」**。 （加入單引號中是否有空格的名稱。）請參閱[Azure 區域](https://azure.microsoft.com/regions/)如需詳細資訊。 |
   | -ResourceGroupName |用於此部署的資源群組名稱。 |
   | -UploadArtifacts |此參數存在時，指定要從本機系統上傳至 Azure 的成品。 您只需要設定此參數，如果您的範本部署需要額外的成品，您想要使用 PowerShell 指令碼 （例如組態指令碼或巢狀的範本） 的階段。 |
   | -StorageAccountName |用於此部署階段成品的儲存體帳戶名稱。 如果您預備部署的成品，才使用這個參數。 如果提供這個參數，如果指令碼尚未建立在先前的部署期間建立新的儲存體帳戶。 如果指定的參數，則必須已經存在儲存體帳戶。 |
   | -StorageAccountResourceGroupName |儲存體帳戶相關聯的資源群組名稱。 只有當您提供 StorageAccountName 參數的值時，才需要此參數。 |
   | -TemplateFile |在 Azure 資源群組部署專案範本檔案的路徑。 為了提高彈性，使用此參數的 PowerShell 指令碼，而不是絕對路徑的位置相對的路徑。 |
   | -TemplateParametersFile |Azure 資源群組部署專案中的參數檔案路徑。 為了提高彈性，使用此參數的 PowerShell 指令碼，而不是絕對路徑的位置相對的路徑。 |
   | -ArtifactStagingDirectory |此參數可讓的 PowerShell 指令碼知道資料夾從專案的二進位檔複製的目的地。 這個值會覆寫使用 PowerShell 指令碼的預設值。 如需使用 Azure DevOps 服務，將值設定為:-ArtifactStagingDirectory $ （build.stagingdirectory) |
   
   以下是指令碼引數的範例 （斷行以方便閱讀）：
   
   ```    
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json' 
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct' 
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'    
   ```
   
   完成之後，當**指令碼引數**方塊看起來應該像下面清單：
   
   ![指令碼引數][11]
9. 您已加入 Azure PowerShell 建置步驟中的所有必要的項目之後，請選擇**佇列**建置按鈕以建置專案。 **建置**畫面會顯示 PowerShell 指令碼的輸出。

### <a name="detailed-walkthrough-for-option-2"></a>選項 2 的詳細逐步解說
下列程序會引導您在 Azure 的 DevOps 服務使用的內建工作設定連續部署所需的步驟。

1. 編輯您的 Azure DevOps 服務建置管線，來新增兩個新的建置步驟。 選擇組建管線底下**組建定義**類別目錄，然後選擇**編輯**連結。
   
   ![編輯組建定義][12]
2. 將新的建置步驟新增至組建管線使用**新增建置步驟...** 按鈕。
   
   ![加入建置步驟][13]
3. 選擇**部署**工作分類中，選取**Azure File Copy**工作，並再選擇其**新增** 按鈕。
   
   ![將 Azure 檔案複製工作][14]
4. 選擇**Azure 資源群組部署**工作，然後選擇其**新增** 按鈕，然後**關閉****工作目錄**。
   
   ![將 Azure 資源群組部署工作][15]
5. 選擇**Azure 檔案複製**工作，並填入其值。
   
   如果您已經有 Azure 服務端點新增至 Azure 的 DevOps 服務，選擇訂用帳戶**Azure 訂用帳戶**下拉式清單方塊。 如果您沒有訂用帳戶，請參閱[選項 1](#detailed-walkthrough-for-option-1)的其中一個設定 Azure DevOps 服務中的指示。
   
   * 來源-輸入 **$ （build.stagingdirectory)**
   * Azure 的連線類型-選取**Azure Resource Manager**
   * Azure RM 訂用帳戶-選取您想要在中使用的儲存體帳戶的訂用帳戶**Azure 訂用帳戶**下拉式清單方塊。 如果訂用帳戶未出現，請選擇**重新整理**按鈕旁**管理**連結。
   * 目的地類型-選取**Azure Blob**
   * RM 儲存體帳戶-選取的儲存體帳戶，您想要針對預備構件使用
   * 容器名稱-輸入您想要用於暫存; 容器名稱它可以是任何有效的容器名稱，但使用一個專門用於此組建管線
   
   輸出值：
   
   * 儲存體容器 URI-輸入**artifactsLocation**
   * 儲存體容器 SAS 權杖-輸入**artifactsLocationSasToken**
   
   ![設定 Azure 檔案複製工作][16]
6. 選擇**Azure 資源群組部署**組建步驟，然後填入其值。
   
   * Azure 的連線類型-選取**Azure Resource Manager**
   * Azure RM 訂用帳戶-選取的訂用帳戶中部署**Azure 訂用帳戶**下拉式清單方塊。 這通常會在上一個步驟中使用的相同訂用帳戶
   * 動作-選取**建立或更新資源群組**
   * 資源群組-選取資源群組，或輸入部署新的資源群組名稱
   * 位置-選取資源群組的位置
   * 範本-輸入要部署範本的名稱與路徑前面加上 **$ （build.stagingdirectory)**，例如： **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * 範本參數-輸入要使用的參數名稱與路徑前面加上 **$ （build.stagingdirectory)**，例如： **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * 覆寫範本參數-輸入或複製並貼上下列程式碼：
     
     ```    
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![設定 Azure 資源群組部署工作][17]
7. 新增所有必要的項目之後，儲存組建管線，並選擇**新的組建排入佇列**頂端。

## <a name="next-steps"></a>後續步驟
讀取[Azure Resource Manager 概觀](/azure-resource-manager/resource-group-overview.md)若要深入了解 Azure Resource Manager 和 Azure 資源群組。

[0]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png
[1]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png
[2]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png
[3]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png
[4]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png
[5]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png
[8]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png
[9]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png
[10]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png
[11]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png
[12]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png
[13]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png
[14]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png
[15]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png
[16]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png
[17]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png
