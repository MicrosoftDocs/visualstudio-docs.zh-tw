---
title: 設定具名的驗證認證 | Microsoft Docs
description: 了解如何提供 Visual Studio 可用來向 Azure 驗證要求的認證，以便您可以將應用程式從 Visual Studio 發佈至 Azure，或用來監視現有的雲端服務。
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: bd4c1864539d915e34b286debb3f6b2f739049d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843796"
---
# <a name="set-up-named-authentication-credentials"></a>設定具名驗證認證

若要將應用程式發佈至 Azure，或監控現有的雲端服務，Visual Studio 會要求認證，以便向 Azure 驗證要求，也就是您的 Azure 訂用帳戶識別碼，以及具有至少 2048 位元金鑰的有效 X.509 v3 憑證。 您可以透過下列任一方法提供這些認證︰

- 在 Visual Studio 中，選取 [檢視] > [伺服器總管]，以滑鼠右鍵按一下 [Azure] 節點，選取 [連線至 Microsoft Azure 訂用帳戶]，然後登入。
- 建立訂用帳戶檔案 (`.publishsettings`)，其包含憑證的公開金鑰。 訂用帳戶檔案可以包含多個訂用帳戶的認證，如本文所述。

注意：這些認證與用來驗證對 Azure 儲存體服務要求的認證不同。

## <a name="create-a-subscription-file"></a>建立訂用帳戶檔案

在 [伺服器總管] 中，以滑鼠右鍵按一下 [Azure] 節點，然後選取 [管理及篩選訂閱]。 接著，選取 [憑證] 索引標籤，然後進行下列任一操作：

- 選取 [匯入] 以開啟 [匯入 Microsoft Azure 訂用帳戶] 對話方塊。 選取 [下載訂用帳戶檔案] 連結，然後在瀏覽器中，將下載的檔案儲存至暫存位置。 返回對話方塊，瀏覽至下載位置，然後將其匯入以用於驗證。
- 選擇使用中的訂用帳戶，然後選取 [編輯]，隨即會開啟一個對話方塊，您可以從中編輯現有訂用帳戶，以用於驗證。
- 選取 [新增] 以開啟 [新增訂用帳戶] 對話方塊，並提供所需的詳細資料。 若要將憑證上傳至對話方塊中所指的雲端服務，請登入 Azure 入口網站，瀏覽至您的雲端服務，選取 [設定] > [管理憑證]，選取 [上傳]，然後指定 `.cer` 檔案的路徑。

如果您想要自行建立憑證，您可以參考[建立及上傳 Azure 的管理憑證](/azure/cloud-services/cloud-services-certs-create)中的指示，然後手動將憑證上傳至 [Azure 入口網站](https://portal.azure.com/)。

## <a name="next-steps"></a>下一步

- [Web Apps 的一般概觀](/azure/app-service/)
- [將您的應用程式部署至 Azure App Service](/azure/app-service/app-service-deploy-local-git)
- [使用 Visual Studio 部署 WebJob](/azure/app-service/websites-dotnet-deploy-webjobs)
- [建立及部署雲端服務](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
