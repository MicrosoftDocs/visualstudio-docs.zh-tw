---
title: 部署概觀 | Microsoft Docs
ms.custom: seodec18
ms.date: 06/22/2018
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdf11d31244ffca5c6a12e0661d34a8727301be0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952596"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Visual Studio 中的部署概觀

透過部署應用程式、服務或元件，就可以將它散發到其他電腦、裝置、伺服器或雲端上進行安裝。 請在 Visual Studio 中針對您需要的部署類型選擇適當的方法。

針對許多常見的應用程式類型，您可以直接從 Visual Studio 中的 [方案總管] 來部署應用程式。 如需這項功能的快速導覽，請參閱[部署簡介](../deployment/deploying-applications-services-and-components.md)。

![選擇發行選項](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>適合我的發行選項為何？

在 Visual Studio 內，可以直接將應用程式發行至下列目標：

- [Azure App Service](#azure-app-service)
- [Azure 虛擬機器](#azure-virtual-machines)
- [檔案系統](#file-system)
- [自訂目標 (IIS、FTP 等)](#custom-targets)，包含所有任意 Web 伺服器。

在 [發行] 索引標籤上，您可以選取現有的發行設定檔、匯入現有的發行設定檔，或使用這裡所述的選項建立新的發行設定檔。 若要了解 IDE 中不同應用程式類型的發佈選項，請參閱[部署簡介](../deployment/deploying-applications-services-and-components.md)。

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) 和 [Linux 上的 App Service](/azure/app-service/containers/app-service-linux-intro) 可協助開發人員快速建立各種可調整的 Web 應用程式和服務，而不需要維護基礎結構。

您可以透過為上層 App Service 選擇[定價層或方案](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)，來決定 App Service 計算能力的強弱。 您可以讓多個 Web 應用程式 (及其他應用程式類型) 共用相同的 App Service，而不需變更定價層。 例如，您可以在相同的 App Service 上同時裝載開發、預備和生產 Web 應用程式。

App Service 會在 Azure 中裝載雲端的虛擬機器上執行，並自動管理這些虛擬機器。 App Service 中每個應用程式都會獲指派唯一的 \*.azurewebsites.net URL；「免費」以外的所有定價層都允許為網站指派自訂網域名稱。

### <a name="when-to-choose-azure-app-service"></a>選擇 Azure App Service 的時機

- 您想要部署可透過網際網路存取的 Web 應用程式。
- 您想要依據需求自動調整 Web 應用程式，而不需要重新部署。
- 您不想要維護伺服器基礎結構 (包括軟體更新)。
- 您不需要在裝載 Web 應用程式的伺服器上進行任何電腦層級自訂。

> 如果您想要在自己的資料中心或其他內部部署電腦中使用 Azure App Service，則做法是使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。

如需發行至 App Service 的詳細資訊，請參閱[快速入門 - 發行至 Azure App Service](quickstart-deploy-to-azure.md) 及[快速入門 - 將 ASP.NET Core 發行至 Linux ](quickstart-deploy-to-linux.md)。

## <a name="azure-virtual-machines"></a>Azure 虛擬機器

[Azure 虛擬機器 (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) 可讓您建立和管理雲端中任意數目的計算資源。 假設負有 VM 上所有軟體和更新的責任，即可依應用程式要求視需要進行自訂。 您可以透過「遠端桌面」直接存取虛擬機器，每部機器都會依需要維持其獲指派的 IP 位址。

調整裝載於虛擬機器的應用程式涉及依需求啟動其他 VM，然後部署必要軟體。 這個額外控制層可讓您在全球各地區以不同的方式調整。 例如，如果您的應用程式服務各種地區辦公室的員工，則可以依據這些地區域中的員工數目來調整 VM，而這可能會降低成本。

如需其他資訊，請參閱 Azure App Service、Azure 虛擬機器以及其他 Azure 服務之間的[詳細比較](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/)，而您可以使用 Visual Studio 中的 [自訂] 選項將這些 Azure 服務用作部署目標。

### <a name="when-to-choose-azure-app-virtual-machines"></a>選擇 Azure App 虛擬機器的時機

- 您想要部署可透過網際網路存取的 Web 應用程式，並完整控制所指派 IP 位址的存留期。
- 您需要在伺服器上進行電腦層級自訂，包括特定資料庫系統、特定網路組態、磁碟分割等這類額外軟體。
- 您想要具有調整 Web 應用程式的細部控制層。
- 您因任何其他原因而需要直接存取裝載應用程式的伺服器。

> 如果您想要在自己的資料中心或其他內部部署電腦中使用 Azure 虛擬機器，則做法是使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。

## <a name="file-system"></a>檔案系統

部署至檔案系統，表示只需要將應用程式檔案複製到您自己電腦上的特定資料夾。 這最常用於進行測試；或者，如果電腦也執行伺服器，則用來部署應用程式以供有限數目的人員使用。 如果在網路上共用目標資料夾，則部署至檔案系統之後，其他可能接著將它部署至特定伺服器的人員將可使用 Web 應用程式檔案。

任何正在執行伺服器的本機電腦都可以透過網際網路或內部網路使用應用程式，而這取決於其設定方式和其所連接的網路。 (如果您將電腦直接連線至網際網路，請特別注意保護它免受外部安全性威脅)。因為您可以管理這些電腦，所以可以完全控制軟體和硬體組態。

請注意，如果您因任何原因 (例如電腦存取) 而無法使用 Azure App Service 或 Azure 虛擬機器這類雲端服務，則可以在自己的資料中心內使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。 Azure Stack 既可讓您透過 Azure App Service 和「Azure 虛擬機器」來管理和使用計算資源，又可讓所有項目保留在內部部署環境中。

### <a name="when-to-choose-file-system-deployment"></a>選擇檔案系統部署的時機

- 您只需要將應用程式部署至檔案共用，而其他人將從該檔案共用部署至不同伺服器。
- 您只需要本機測試部署。
- 您想要個別檢查並可能修改應用程式檔案，再將它們傳送至另一個部署目標。

如需詳細資訊，請參閱[快速入門 - 部署到本機資料夾](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>自訂目標 (IIS、FTP)

自訂目標可讓您將應用程式部署至 Azure App Service、Azure 虛擬機器或本機檔案系統以外的目標。 它可以部署至檔案系統或您具有存取權的任何其他伺服器 (網際網路或內部網路)，包括其他雲端服務上的伺服器。 它可以使用 Web 部署 (檔案或 .ZIP) 和 FTP。

選擇自訂目標時，Visual Studio 會提示您輸入設定檔名稱，接著收集其他**連線**資訊，包括目標伺服器或位置、網站名稱和認證。 您可以在 [設定] 索引標籤上控制下列行為：

- 您想要部署的組態。
- 是否要從目的地中移除現有的檔案。
- 是否要在發行時預先編譯。
- 是否要將 [App_Data] 資料夾中的檔案從部署中排除。

您可以在 Visual Studio 中建立任意數目的自訂部署設定檔，這可讓您利用不同的設定來管理設定檔。

### <a name="when-to-choose-custom-deployment"></a>選擇自訂部署的時機

- 您使用可透過 URL 存取的提供者 (非 Azure) 雲端服務。
- 您想要使用認證進行部署，但這些認證不是您在 Visual Studio 內使用的認證或直接繫結至 Azure 帳戶的認證。
- 您想要在每次部署時刪除目標中的檔案。

如需詳細資訊，請參閱[快速入門 - 部署到網站](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>後續步驟

教學課程：

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [將 ASP.NET Core 應用程式發行至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Visual C++ 中的部署](/cpp/ide/deployment-in-visual-cpp)
- [部署 UWP 應用程式](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [使用 Web Deploy 將 Node.js 應用程式發行至 Azure](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [將 Python 應用程式發行至 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
