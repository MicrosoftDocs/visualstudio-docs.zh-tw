---
title: 設定具名的驗證認證 |Microsoft Docs
description: 了解如何提供 Visual Studio 可以用來向 Azure 驗證要求，因此您可以發行至 Azure 的應用程式，從 Visual Studio 或監視現有的雲端服務的認證。
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 6f41ea2072ef5791735fac61205f68151d5a9f7e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001991"
---
# <a name="set-up-named-authentication-credentials"></a>設定具名驗證認證

若要發行至 Azure 的應用程式，或監視現有的雲端服務，Visual Studio 就會需要認證，才能向 Azure 驗證要求，也就是您的 Azure 訂用帳戶識別碼和索引鍵為至少 2048 位元的有效 X.509 v3 憑證。 您提供這些認證透過其中一種下列方法：

- 在 Visual Studio 中，選取**檢視 > 伺服器總管**，以滑鼠右鍵按一下**Azure**節點中，選取**連接到 Microsoft Azure 訂用帳戶**，並登入。
- 建立訂用帳戶檔案 (`.publishsettings`)，其中包含公開金鑰的憑證。 這篇文章中所述，訂用帳戶檔案可以包含多個訂用帳戶的認證。

注意： 這些認證會與用來驗證對 Azure 儲存體服務要求的認證不同。

## <a name="create-a-subscription-file"></a>建立訂用帳戶檔案

在 [伺服器總管] 中，以滑鼠右鍵按一下**Azure**節點，然後選取**管理及篩選訂閱**。 然後選取**憑證**索引標籤，然後再執行下列動作之一：

- 選取 [**匯入**來開啟**匯入 Microsoft Azure 訂用帳戶**] 對話方塊。 選取 **下載訂用帳戶檔案**連結，然後在瀏覽器將下載的檔案儲存到暫存位置。 回到 [] 對話方塊中，瀏覽至下載位置，然後將它匯入以用於驗證。
- 選擇有效的訂用帳戶，然後選取**編輯**，來開啟的對話方塊，您可以在其中編輯現有的訂用帳戶以用於驗證。
- 選取 **新增**來開啟**新的訂用帳戶**對話方塊方塊並提供必要的詳細資料。 若要將憑證上傳至您的雲端服務會註明在對話方塊中，登入 Azure 入口網站，瀏覽至您的雲端服務，選取**設定 > 管理憑證**，選取**上傳**，然後指定的路徑`.cer`檔案。

如果您想要自行建立憑證，您可以參考中的指示[建立及上傳 Azure 管理憑證](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx)然後手動上傳的憑證[Azure 入口網站](https://portal.azure.com/)。

## <a name="next-steps"></a>後續步驟

- [Web 應用程式的一般概觀](https://docs.microsoft.com/azure/app-service/)
- [將您的應用程式部署至 Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [使用 Visual Studio 部署 WebJobs](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [建立和部署雲端服務](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)