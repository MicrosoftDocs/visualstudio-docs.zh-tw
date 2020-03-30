---
title: 無需重新簽名即可部署 ClickOnce 應用
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395327"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>部署 ClickOnce 應用程式以進行測試和生產伺服器，無需重新分配
本文介紹了 .NET Framework 版本 3.5 中引入的 ClickOnce 功能，該功能支援從多個網路位置部署 ClickOnce 應用程式，而無需重新簽名或更改 ClickOnce 清單。

> [!NOTE]
> 重新分配仍然是部署新版本應用程式的首選方法。 只要有可能，請使用重新分配方法。 有關詳細資訊，請參閱[*Mage.exe（* 清單生成和編輯工具）。](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)

 協力廠商開發人員和 ISV 可以加入宣告此功能，從而簡化其客戶更新其應用程式。 此功能可用於以下情況：

- 更新應用程式時，不是應用程式的第一次安裝。

- 當電腦上只有一個應用程式佈建時。 例如，如果應用程式佈建為指向兩個不同的資料庫，則無法使用此功能。

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>從部署清單中排除部署提供程式
 在 .NET 框架 2.0 和 .NET 框架 3.0 中，在系統上安裝以進行離線可用性的任何`deploymentProvider`ClickOnce 應用程式都必須在其部署清單中列出 。 通常`deploymentProvider`稱為更新位置;它是 ClickOnce 檢查應用程式更新的位置。 這一要求，以及應用程式發行者需要簽署其部署，使公司難以更新來自供應商或其他協力廠商的 ClickOnce 應用程式。 它還使在同一網路上的多個位置部署同一應用程式變得更加困難。

 通過對 .NET 框架 3.5 中的 ClickOnce 所做的更改，協力廠商可以將 ClickOnce 應用程式提供給另一個組織，然後該組織可以在自己的網路上部署應用程式。

 為了利用此功能，ClickOnce 應用程式的開發人員必須從其部署清單中排除`deploymentProvider`。 此要求意味著，在使用 Mage.exe 創建部署清單時，必須排除`-providerUrl`參數。 或者，如果要使用 MageUI.exe 生成部署清單，則必須確保 **"應用程式清單**"選項卡上的 **"啟動位置**"文字方塊留空。

## <a name="deploymentprovider-and-application-updates"></a>部署提供程式和應用程式更新
 從 .NET 框架 3.5 開始，您不再需要在部署`deploymentProvider`清單中指定 ，即可部署 ClickOnce 應用程式以用於連線和離線使用。 此更改支援需要自行打包和簽名部署，但允許其他公司在其網路上部署應用程式的方案。

 需要記住的要點是，排除 的`deploymentProvider`應用程式在更新期間無法更改其安裝位置，直到他們再次發佈包含`deploymentProvider`標記的更新。

 下面是兩個示例來闡明這一點。 在第一個示例中，您發佈一`deploymentProvider`個沒有標記的 ClickOnce 應用程式，並要求使用者從`http://www.adatum.com/MyApplication/`安裝該應用程式。 如果您決定要發佈應用程式的`http://subdomain.adatum.com/MyApplication/`下一個更新，則無法在駐留在 的部署清單中`http://www.adatum.com/MyApplication/`表示這一點。 你可以做兩件事之一：

- 告訴使用者卸載以前的版本，並從新位置安裝新版本。

- 包括包含`http://www.adatum.com/MyApplication/``deploymentProvider`指向`http://www.adatum.com/MyApplication/`的更新。 然後，稍後使用`deploymentProvider`指向`http://subdomain.adatum.com/MyApplication/`發佈另一個更新。

  在第二個示例中，您發佈指定`deploymentProvider`的 ClickOnce 應用程式，然後決定刪除它。 將沒有新版本`deploymentProvider`下載到用戶端後，在發佈已`deploymentProvider`還原的應用程式版本之前，無法重定向用於更新的路徑。 與第一個示例一`deploymentProvider`樣，必須最初指向當前更新位置，而不是新位置。 在這種情況下，如果嘗試插入引用`deploymentProvider``http://subdomain.adatum.com/MyApplication/`的 ，則下一次更新將失敗。

## <a name="create-a-deployment"></a>建立部署
 有關創建可以從不同網路位置部署的部署的分步指南，請參閱[演練：手動部署不需要重新簽名並保留品牌資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)。

## <a name="see-also"></a>另請參閱
- [*Mage.exe（* 清單生成和編輯工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe（* 清單生成和編輯工具，圖形用戶端）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
