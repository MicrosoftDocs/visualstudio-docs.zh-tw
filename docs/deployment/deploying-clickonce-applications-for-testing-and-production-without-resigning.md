---
title: 部署 ClickOnce 應用程式但不重新簽署
description: 瞭解如何從多個網路位置部署 ClickOnce 應用程式，而不需要重新簽署或變更 ClickOnce 資訊清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d5d7244f70852dee29813834fc427c888df9c1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912148"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>針對測試和實際執行伺服器部署 ClickOnce 應用程式，而不需進行簽署
本文描述 .NET Framework 版本3.5 中引進的 ClickOnce 功能，可讓您從多個網路位置部署 ClickOnce 應用程式，而不需要重新簽署或變更 ClickOnce 資訊清單。

> [!NOTE]
> 在部署新版本的應用程式時，仍是慣用的方法。 可能的話，請使用「讓步」方法。 如需詳細資訊，請參閱 [ *Mage.exe* (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)。

 協力廠商開發人員和 Isv 可以加入宣告這項功能，讓客戶更輕鬆地更新應用程式。 這項功能可用於下列情況：

- 更新應用程式時，不會在第一次安裝應用程式時使用。

- 當電腦上只有一個應用程式設定時。 例如，如果將應用程式設定為指向兩個不同的資料庫，您就無法使用這項功能。

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>從部署資訊清單排除 deploymentProvider
 在 .NET Framework 2.0 和 .NET Framework 3.0 中，安裝在系統上以供離線使用的任何 ClickOnce 應用程式都必須 `deploymentProvider` 在其部署資訊清單中列出。 `deploymentProvider`通常稱為更新位置，它是 ClickOnce 檢查應用程式更新的位置。 這項需求，以及應用程式發行者簽署其部署的需求，讓公司難以從廠商或其他協力廠商更新 ClickOnce 應用程式。 它也會讓您更難從相同網路上的多個位置部署相同的應用程式。

 在 .NET Framework 3.5 中對 ClickOnce 進行的變更時，協力廠商可能會將 ClickOnce 應用程式提供給另一個組織，然後將應用程式部署在自己的網路上。

 為了充分利用此功能，ClickOnce 應用程式的開發人員必須 `deploymentProvider` 從其部署資訊清單中排除。 這項需求表示 `-providerUrl` 當您使用 Mage.exe 建立部署資訊清單時，必須排除引數。 或者，如果您要使用 MageUI.exe 產生部署資訊清單，您必須確定 [**應用程式資訊清單**] 索引標籤上的 [**啟動位置**] 文字方塊保持空白。

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider 和應用程式更新
 從 .NET Framework 3.5 開始，您不再需要在部署資訊清單中指定，就能 `deploymentProvider` 同時部署 ClickOnce 應用程式以進行線上和離線使用。 這種變更支援您必須自行封裝和簽署部署的情況，但允許其他公司透過其網路部署應用程式。

 要記住的重點是，排除 a 的應用程式 `deploymentProvider` 在更新期間無法變更其安裝位置，直到他們送出包含標記的更新為止 `deploymentProvider` 。

 以下是兩個範例來說明這一點。 在第一個範例中，您會發佈沒有標記的 ClickOnce 應用程式 `deploymentProvider` ，並要求使用者從安裝該應用程式 `http://www.adatum.com/MyApplication/` 。 如果您決定要從發行應用程式的下一個更新 `http://subdomain.adatum.com/MyApplication/` ，您就無法在位於的部署資訊清單中表示這種情況 `http://www.adatum.com/MyApplication/` 。 您可以執行下列兩項作業之一：

- 告訴您的使用者卸載舊版，然後從新的位置安裝新的版本。

- 包含的更新 `http://www.adatum.com/MyApplication/` ，其中包含 `deploymentProvider` 指向的 `http://www.adatum.com/MyApplication/` 。 然後，稍後再以指向的方式發行另一個更新 `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` 。

  在第二個範例中，您會發佈指定的 ClickOnce 應用程式， `deploymentProvider` 然後決定將它移除。 一旦將新版本 `deploymentProvider` 下載到用戶端之後，您就無法重新導向用於更新的路徑，直到您發行已還原的應用程式版本為止 `deploymentProvider` 。 和第一個範例一樣，一 `deploymentProvider` 開始必須指向目前的更新位置，而不是新的位置。 在此情況下，如果您嘗試插入 `deploymentProvider` 參考的 `http://subdomain.adatum.com/MyApplication/` ，則下一個更新會失敗。

## <a name="create-a-deployment"></a>建立部署
 如需建立可從不同網路位置部署之部署的逐步指引，請參閱逐步解說 [：手動部署不需要重新簽署的 ClickOnce 應用程式，並保留商標資訊](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)。

## <a name="see-also"></a>另請參閱
- [*Mage.exe* (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (資訊清單產生和編輯工具、圖形用戶端)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
