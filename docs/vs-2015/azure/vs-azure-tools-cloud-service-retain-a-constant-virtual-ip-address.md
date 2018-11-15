---
title: 如何保持 Azure 雲端服務的固定虛擬 IP 位址 |Microsoft Docs
description: 了解如何確保您的 Azure 雲端服務的虛擬 IP 位址 (VIP) 不會變更。
author: ghogen
manager: douge
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e74cc5b9bbbfea92d2dea2c00ee5b0f98dc02f21
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001980"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>為 Azure 雲端服務保留常數虛擬 IP 位址
當您更新裝載於 Azure 雲端服務時，您可能需要確保服務的虛擬 IP 位址 (VIP) 不會變更。 許多網域管理服務使用網域名稱系統 (DNS) 註冊網域名稱。 DNS 只有在 VIP 保持不變。 您可以使用**發行精靈**Azure 工具，以確保您的雲端服務的 VIP 不會變更當您更新它。 如需如何使用 DNS 網域管理的雲端服務的詳細資訊，請參閱[設定 Azure 雲端服務的自訂網域名稱](/azure/cloud-services/cloud-services-custom-domain-name-portal)。

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>發佈雲端服務，而不變更其 VIP
當您第一次將它部署至 Azure 特定的環境，例如生產環境中，會配置雲端服務的 VIP。 只有當您明確刪除部署，或由部署更新程序隱含地刪除部署時，才會變更 VIP。 若要保留 VIP，您不能刪除您的部署，您必須先確定 Visual Studio 不會自動刪除您的部署。 

您可以指定部署設定，在**發行精靈**，可支援多種部署選項。 您可以指定全新部署或更新部署，它可以是累加或同時。 這兩種更新部署都會保留 VIP。 如需定義這些不同類型的部署，請參閱[發佈 Azure 應用程式精靈](vs-azure-tools-publish-azure-application-wizard.md)。 此外，您可以控制是否要在發生錯誤時，刪除先前部署的雲端服務。 如果您沒有正確設定該選項，VIP 可能會意外變更。

## <a name="update-a-cloud-service-without-changing-its-vip"></a>更新雲端服務，而不變更其 VIP
1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。 

2. 在 [**方案總管] 中**，以滑鼠右鍵按一下專案。 在快速鍵功能表中，選取**發佈**。

    ![發行功能表](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. 在 **發佈 Azure 應用程式**對話方塊方塊中，選取您要部署的 Azure 訂用帳戶。 登入，如果有必要，然後選取**下一步**。

    ![發佈 Azure 應用程式登入頁面](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. 上**一般設定**索引標籤上，確認您要部署服務雲端的名稱，則**環境**，則**組建組態**，和**服務組態**全都正確無誤。

    ![發佈 Azure 應用程式通用設定索引標籤](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. 在上**進階設定**索引標籤上，確認**部署標籤**並**儲存體帳戶**正確無誤。 確認**刪除失敗的部署** 核取方塊已清除，並確認**部署更新**選取核取方塊。 藉由清除**刪除失敗的部署**您核取方塊，確保您的 VIP 部署期間發生錯誤時不會遺失。 藉由選取**部署更新**核取方塊，您確定不會刪除您的部署，而且不會遺失 VIP 當您重新發佈您的應用程式。 

    ![發佈 Azure 應用程式進階設定 索引標籤](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. 若要進一步指定您希望更新角色的方式，請選取**設定**旁**部署更新**。 選取**累加式更新**或是**同時更新**，然後選取**確定**。 選擇**累加式更新**來更新您的應用程式的每個執行個體逐一，使應用程式一律可供使用。 選擇**同時更新**來更新您的應用程式，在同一時間的所有執行個體。 同時更新較為快速，但您的服務可能無法在更新程序期間。 當您完成時，請選取**下一步**。

    ![發佈 Azure 應用程式部署設定 頁面](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. 在 [**發佈 Azure 應用程式**對話方塊方塊中，選取**下一步]** 直到**摘要**頁面隨即顯示。 請確認您的設定，然後按**發佈**。
   
    ![發佈 Azure 應用程式摘要頁面](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>後續步驟
- [使用 Visual Studio 發佈 Azure 應用程式精靈](vs-azure-tools-publish-azure-application-wizard.md)

