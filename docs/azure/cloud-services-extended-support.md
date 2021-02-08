---
title: '使用雲端服務 (延伸支援)  (Preview) '
description: '立即瞭解如何使用 Azure Resource Manager 搭配 Visual Studio，建立及部署雲端服務 (延伸支援) '
author: ghogen
manager: jmartens
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 39a76f4c76afb2ed0c738adfc477807eebfdbc61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841129"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio-preview"></a>在 Visual Studio (Preview 中建立並部署至雲端服務 (延伸支援) ) 

從 [Visual Studio 2019 16.9 版](https://visualstudio.microsoft.com/vs/preview) (目前為預覽) ，您可以使用 Azure Resource Manager 來使用雲端服務，這可大幅簡化及將其現代化 Azure 資源的維護和管理作業。 這項功能是由稱為「雲端服務」的新 Azure 服務 *(延伸支援)*。 您可以將現有雲端服務發行至雲端服務 (延伸支援) 。 如需此 Azure 服務的詳細資訊，請參閱 [雲端服務 (延伸支援) 檔](/azure/cloud-services-extended-support/overview)。

## <a name="publish-to-cloud-services-extended-support"></a>發佈至雲端服務 (延伸支援) 

當您將現有的 Azure 雲端服務專案發行至雲端服務時 (延伸支援) ，您仍然可以保留發行至傳統 Azure 雲端服務的功能。 在 Visual Studio 2019 16.9 Preview 3 （含）以後版本中，傳統雲端服務專案具有特殊版本的 **發佈** 命令， **發佈 (延伸支援)**。 此命令會出現在 **方案總管** 的快捷方式功能表中。

當您發佈至雲端服務 (延伸支援) 時，會有一些差異。 例如，系統不會詢問您是否要發行至 **預備** 或 **生產環境**，因為這些部署位置不是延伸支援發佈模型的一部分。 相反地，透過雲端服務 (延伸支援) ，您可以設定多個部署，然後在 Azure 入口網站中交換部署。 雖然 Visual Studio 的工具可讓您在 16.9 Preview 3 中進行設定，但在較新版本的雲端服務 (延伸支援) 之前，將不會啟用交換功能，而且可能會在預覽期間導致部署期間發生失敗。

將傳統的 Azure 雲端服務發佈至雲端服務 (延伸支援) 之前，請檢查您的專案所使用的儲存體帳戶，並確定其為儲存體 V1 或儲存體 V2 帳戶。 傳統儲存體帳戶類型會在部署時失敗，並顯示錯誤訊息。 請務必檢查診斷所使用的儲存體帳戶。 若要檢查診斷儲存體帳戶，請參閱 [設定 Azure 雲端服務和虛擬機器的診斷](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)。 如果您的服務使用傳統儲存體帳戶，您可以將它升級;請參閱 [升級為一般用途 v2 儲存體帳戶](/azure/storage/common/storage-account-upgrade?tabs=azure-portal)。  如需儲存體帳戶類型的一般資訊，請參閱 [儲存體帳戶總覽](/azure/storage/common/storage-account-overview)。

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>將傳統的 Azure 雲端服務專案發佈至雲端服務 (延伸支援) 

1. 雲端服務 (延伸支援) 目前為預覽狀態。 註冊訂用帳戶的功能，如下所示：

   ```azurepowershell-interactive
   Register-AzProviderFeature -FeatureName CloudServices -ProviderNamespace Microsoft.Compute
   ```

1. 在 Azure 雲端服務中的專案節點上按一下滑鼠右鍵， (傳統) 專案]，然後選擇 [ **發行 (延伸支援) ...**]。[ **發行] 嚮導** 會在第一個畫面上開啟。

   ![從功能表中選擇 [發行 (延伸支援) ](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   [ **發佈** 嚮導] 隨即出現。

   ![登入頁面](./media/cloud-services-extended-support/publish-step1.png)

1. **帳戶** - 選取帳戶或選取帳戶下拉式清單中的 [新增帳戶]。

1. **選擇您的訂用帳戶** - 選擇要用於部署的訂用帳戶。

1. 選擇 [ **下一步]** 移至 [ **設定** ] 頁面。

   ![一般設定](./media/cloud-services-extended-support/publish-settings.png)

1. **雲端服務 (延伸支援)** -使用下拉式清單，選取現有的雲端服務 (延伸支援) ，或選取 [ **建立新** 的]，然後建立一個。 資料中心會在每個雲端服務的括弧中顯示 (延伸支援) 。 建議雲端服務的資料中心位置 (延伸支援) 與儲存體帳戶的資料中心位置相同。

   如果您選擇建立新的服務，您會看到 [ **建立雲端服務 (延伸支援)** ] 對話方塊。 指定您要用於雲端服務的位置和資源群組 (延伸支援) 。

   ![ (延伸支援) 建立雲端服務](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **建置組態** - 選取 [偵錯] 或 [發行]。

1. **服務組態** - 選取 [雲端] 或 [本機]。

1. **儲存體帳戶** -選取要用於此部署的儲存體帳戶，或 **建立新** 的以建立儲存體帳戶。 區域會針對每個儲存體帳戶顯示在括弧中。 建議使儲存體帳戶的資料中心位置與雲端服務的資料中心位置相同 (一般設定)。

   Azure 儲存體帳戶會儲存應用程式部署的封裝。

1. **Key vault** -指定包含這個雲端服務之秘密的金鑰保存庫 (延伸支援) 。 如果啟用遠端桌面，或將憑證新增至設定，則會啟用此功能。

1. **啟用所有角色的遠端桌面**：如果您想要從遠端連線到服務，請選取此選項。 系統會要求您指定認證。

   ![遠端桌面設定](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. 選擇 [ **下一步]** 移至 [ **診斷設定** ] 頁面。

   ![診斷設定](./media/cloud-services-extended-support/diagnostics-settings.png)

   診斷可讓您針對 Azure 雲端服務 (延伸支援) 進行疑難排解。 如需診斷的相關資訊，請參閱[為 Azure 雲端服務和虛擬機器設定診斷功能](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)。 如需 Application Insights 的相關資訊，請參閱[什麼是 Application Insights？](/azure/application-insights/app-insights-overview)。

1. 選擇 [ **下一步]** 以移至 [ **摘要** ] 頁面。

   ![摘要](./media/cloud-services-extended-support/publish-summary.png)

1. **目標設定檔** - 您可以選擇從您所選擇的設定建立發行設定檔。 例如，您可能會建立一個設定檔用於測試環境，並建立另一個用於生產。 若要儲存這個設定檔，請選擇 [**儲存**] 圖示。 此精靈會建立設定檔並將它儲存在 Visual Studio 專案。 若要修改設定檔名稱，請開啟 [目標設定檔] 清單，然後選擇 [**管理...]**。

   > [!Note]
   > 發行設定檔會顯示在 Visual Studio 的方案總管中，並將設定檔設定寫入副檔名為 *副檔名為 .azurepubxml* 的檔案。 設定會儲存為 XML 標記的屬性。

1. 設定專案部署的所有設定後，請選取對話方塊底部的 [發佈]。 您可以在 Visual Studio 的 [ **Azure 活動記錄** ] 輸出視窗中，監視進程狀態。 選擇 [ **在入口網站中開啟** ] 連結 

恭喜！ 您已將雲端服務 (延伸支援) 專案發佈至 Azure。 若要使用相同的設定再次發行，您可以重複使用發行設定檔，或重複這些步驟來建立新的設定檔。 用於部署的 Azure Resource Manager (ARM) 範本和參數會儲存在 *bin/ \<configuration\> /Publish* 資料夾中。

## <a name="clean-up-azure-resources"></a>清除 Azure 資源

若要清除您遵循本教學課程所建立的 Azure 資源，請移至 [Azure 入口網站](https://portal.azure.com)，選擇 [ **資源群組**]，然後尋找並開啟您用來建立雲端服務的資源群組 (延伸支援) ，然後選擇 [ **刪除資源群組**]。

## <a name="next-steps"></a>下一步

使用 [**發佈**] 畫面上的 [設定 **] 按鈕，** 設定 (CI) 的持續整合。 如需詳細資訊，請參閱 [Azure Pipelines 檔](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)。
