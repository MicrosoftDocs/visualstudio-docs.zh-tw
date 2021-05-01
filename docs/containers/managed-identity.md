---
title: 如何使用具有 Bridge 的受控識別來 Kubernetes
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: 瞭解如何在 AKS 叢集中使用 Azure Active Directory (Azure AD) 的受控識別，並使用 Bridge 來 Kubernetes
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335086"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>使用具有 Bridge 的受控識別來 Kubernetes

如果您的 AKS 叢集使用 [受控識別](/azure/active-directory/managed-identities-azure-resources/overview) 安全性功能來保護對秘密和資源的存取，則 Bridge 到 Kubernetes 需要一些特殊的設定，以確保它可以使用這些功能。 Azure Active Directory (AD) token 必須下載到本機電腦，以確保本機執行和偵測都受到適當的保護，而且這需要在 Bridge 中進行某些特殊設定才能 Kubernetes。 本文說明如何將橋接器設定為 Kubernetes，以使用受控識別的服務。

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>如何設定服務以使用受控識別

若要啟用支援受控識別的本機電腦，請在 *KubernetesLocalConfig. yaml* 檔案的 [新增] `enableFeatures` 區段中 `ManagedIdentity` 。 `enableFeatures`如果區段尚未存在，請新增該區段。

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> 使用開發叢集（而非生產叢集）時，請務必只使用 Kubernetes 的受控識別，因為會將 Azure AD 權杖提取至本機電腦，而這會帶來潛在的安全性風險。

如果您沒有 *KubernetesLocalConfig yaml* 檔案，您可以建立一個檔案;請參閱 [如何：將橋接器設定為 Kubernetes](configure-bridge-to-kubernetes.md)。

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>如何提取 Azure Active Directory 的權杖

您必須在提取權杖時，確定您依賴 <xref:Azure.Identity.DefaultAzureCredential> 或 <xref:Azure.Identity.ManagedIdentityCredential> 在程式碼中。

下列 c # 程式碼顯示當您使用時，如何提取儲存體帳號憑證 `ManagedIdentityCredential` ：

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

下列程式碼示範當您使用 DefaultAzureCredential 時，如何提取儲存體帳號憑證：

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

若要瞭解如何使用受控識別存取其他 Azure 資源，請參閱 [後續步驟](#next-steps) 一節。

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>在權杖下載時接收 Azure 警示

當您使用 Bridge 在服務上 Kubernetes 時，Azure AD 權杖會下載到本機電腦。 您可以讓 Azure 警示在發生這種情況時收到通知。 如需詳細資訊，請參閱 [啟用 Azure Defender](/azure/security-center/enable-azure-defender)。 請注意，在30天的試用期) 之後 (收費。

## <a name="next-steps"></a>下一步

現在您已將 Bridge 設定為 Kubernetes，以使用受控識別的 AKS 叢集，您可以正常地進行調試。 請參閱 [kubernetes]，以連線至您的叢集和偵測-服務]。

若要深入瞭解如何使用受控識別來存取 Azure 資源，請遵循下列教學課程：

- [教學課程：使用 Linux VM 系統指派的受控識別來存取 Azure 儲存體](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [教學課程：使用 Linux VM 系統指派的受控識別來存取 Azure Data Lake Store](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [教學課程：使用 VM 系統指派的受控識別來存取 Azure Key Vault](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

本節也有其他教學課程，可讓您使用受控識別來存取其他 Azure 資源。

## <a name="see-also"></a>另請參閱

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
