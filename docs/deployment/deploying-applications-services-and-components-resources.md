---
title: 將您的 Visual Studio 應用程式部署到資料夾、IIS、Azure 或其他目的地
description: 深入瞭解如何使用發佈嚮導發佈應用程式的選項
ms.custom: contperfq1
ms.date: 08/21/2020
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
ms.openlocfilehash: 7125be46a894072f034bf1fce3060d2bda564aff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800825"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>將您的應用程式部署到資料夾、IIS、Azure 或其他目的地

透過部署應用程式、服務或元件，就可以將它散發到其他電腦、裝置、伺服器或雲端上進行安裝。 請在 Visual Studio 中針對您需要的部署類型選擇適當的方法。

針對許多常見的應用程式類型，您可以直接從 Visual Studio 中的 [方案總管] 來部署應用程式。 如需這項功能的快速導覽，請參閱[部署簡介](../deployment/deploying-applications-services-and-components.md)。

![選擇發佈選項](../deployment/media/quickstart-publish-dialog.png)

## <a name="what-publishing-options-are-right-for-me"></a>適合我的發行選項為何？

在 Visual Studio 內，可以直接將應用程式發行至下列目標：

- [Azure](#azure)
- [Docker Container Registry](#docker-container-registry)
- [資料夾](#folder)
- [FTP/FTPS 伺服器](#ftpftps-server)
- [Web 服務器 (IIS) ](#web-server-iis)
- [匯入設定檔](#import-profile)

## <a name="azure"></a>Azure 

當您選擇 Azure 時，可以選擇：

- 在 Windows、Linux 或 Docker 映射上執行 Azure App Service
- 部署至 Azure Container Registry 的 Docker 映射
- Azure 虛擬機器

![選擇 Azure 服務](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) 可協助開發人員快速建立可擴充的 web 應用程式和服務，而不需要維護基礎結構。 App Service 會在 Azure 中裝載雲端的虛擬機器上執行，並自動管理這些虛擬機器。 App Service 中每個應用程式都會獲指派唯一的 \*.azurewebsites.net URL；「免費」以外的所有定價層都允許為網站指派自訂網域名稱。

您可以透過為上層 App Service 選擇[定價層或方案](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)，來決定 App Service 計算能力的強弱。 您可以讓多個 Web 應用程式 (及其他應用程式類型) 共用相同的 App Service，而不需變更定價層。 例如，您可以在相同的 App Service 上同時裝載開發、預備和生產 Web 應用程式。

#### <a name="when-to-choose-azure-app-service"></a>選擇 Azure App Service 的時機

- 您想要部署可透過網際網路存取的 Web 應用程式。
- 您想要依據需求自動調整 Web 應用程式，而不需要重新部署。
- 您不想要維護伺服器基礎結構 (包括軟體更新)。
- 您不需要在裝載 Web 應用程式的伺服器上進行任何電腦層級自訂。

> 如果您想要在自己的資料中心或其他內部部署電腦中使用 Azure App Service，則做法是使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。

如需發行至 App Service 的詳細資訊，請參閱：
- [快速入門-發佈至 Azure App Service](quickstart-deploy-to-azure.md) 並 [快速入門-將 ASP.NET Core 發佈至 Linux](quickstart-deploy-to-linux.md)。
- [疑難排解 Azure App Service 和 IIS 上的 ASP.NET Core](/aspnet/core/test/troubleshoot-azure-iis)。

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) 可讓您在私人登錄中建立、儲存及管理所有容器部署類型的 Docker 容器映射和構件。

#### <a name="when-to-choose-azure-container-registry"></a>選擇 Azure Container Registry 的時機

- 當您有現有的 Docker 容器開發和部署管線時。
- 當您想要在 Azure 中建立 Docker 容器映射時。

### <a name="azure-virtual-machines"></a>Azure 虛擬機器

[Azure 虛擬機器 (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) 可讓您建立和管理雲端中任意數目的計算資源。 假設負有 VM 上所有軟體和更新的責任，即可依應用程式要求視需要進行自訂。 您可以透過「遠端桌面」直接存取虛擬機器，每部機器都會依需要維持其獲指派的 IP 位址。

調整裝載於虛擬機器的應用程式涉及依需求啟動其他 VM，然後部署必要軟體。 這個額外控制層可讓您在全球各地區以不同的方式調整。 例如，如果您的應用程式服務各種地區辦公室的員工，則可以依據這些地區域中的員工數目來調整 VM，而這可能會降低成本。

如需其他資訊，請參閱 Azure App Service、Azure 虛擬機器以及其他 Azure 服務之間的[詳細比較](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/)，而您可以使用 Visual Studio 中的 [自訂] 選項將這些 Azure 服務用作部署目標。

#### <a name="when-to-choose-azure-virtual-machines"></a>選擇 Azure 虛擬機器的時機

- 您想要部署可透過網際網路存取的 Web 應用程式，並完整控制所指派 IP 位址的存留期。
- 您需要在伺服器上進行電腦層級自訂，包括特定資料庫系統、特定網路組態、磁碟分割等這類額外軟體。
- 您想要具有調整 Web 應用程式的細部控制層。
- 您因任何其他原因而需要直接存取裝載應用程式的伺服器。

> 如果您想要在自己的資料中心或其他內部部署電腦中使用 Azure 虛擬機器，則做法是使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。

## <a name="docker-container-registry"></a>Docker Container Registry

如果您的應用程式使用 Docker，您可以將容器化應用程式發佈至 Docker Container Registry。

### <a name="when-to-choose-docker-container-registry"></a>選擇 Docker Container Registry 的時機

- 您想要部署容器化應用程式

## <a name="folder"></a>資料夾

部署至檔案系統，表示只需要將應用程式檔案複製到您自己電腦上的特定資料夾。 這最常用於進行測試；或者，如果電腦也執行伺服器，則用來部署應用程式以供有限數目的人員使用。 如果在網路上共用目標資料夾，則部署至檔案系統之後，其他可能接著將它部署至特定伺服器的人員將可使用 Web 應用程式檔案。

任何正在執行伺服器的本機電腦都可以透過網際網路或內部網路使用應用程式，而這取決於其設定方式和其所連接的網路。  (如果您將電腦直接連線到網際網路，請特別小心保護它免于遭受外部安全性威脅。 ) 因為您管理這些機器，所以您完全掌控軟體和硬體設定。

請注意，如果您因任何原因 (例如電腦存取) 而無法使用 Azure App Service 或 Azure 虛擬機器這類雲端服務，則可以在自己的資料中心內使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。 Azure Stack 既可讓您透過 Azure App Service 和「Azure 虛擬機器」來管理和使用計算資源，又可讓所有項目保留在內部部署環境中。

### <a name="when-to-choose-file-system-deployment"></a>選擇檔案系統部署的時機

- 您只需要將應用程式部署至檔案共用，而其他人將從該檔案共用部署至不同伺服器。
- 您只需要本機測試部署。
- 您想要個別檢查並可能修改應用程式檔案，再將它們傳送至另一個部署目標。

如需詳細資訊，請參閱[快速入門 - 部署到本機資料夾](quickstart-deploy-to-local-folder.md)

## <a name="ftpftps-server"></a>FTP/FTPS 伺服器

FTP/FTPS 伺服器可讓您將應用程式部署至 Azure 以外的伺服器。 它可以部署至檔案系統或您具有存取權的任何其他伺服器 (網際網路或內部網路)，包括其他雲端服務上的伺服器。 它可以使用 Web 部署 (檔案或 .ZIP) 和 FTP。

選擇 FTP/FTPS 伺服器時，Visual Studio 會提示您輸入設定檔名稱，然後收集其他 **連接** 資訊，包括目標伺服器或位置、網站名稱和認證。 您可以在 [設定]**** 索引標籤上控制下列行為：

- 您想要部署的組態。
- 是否要從目的地中移除現有的檔案。
- 是否要在發行時預先編譯。
- 是否要將 [App_Data] 資料夾中的檔案從部署中排除。

您可以在 Visual Studio 中建立任意數目的 FTP/FTPS 部署設定檔，讓您可以使用不同的設定來管理設定檔。

### <a name="when-to-choose-ftpftps-server-deployment"></a>選擇 FTP/FTPS 伺服器部署的時機

- 您使用可透過 URL 存取的提供者 (非 Azure) 雲端服務。
- 您想要使用認證進行部署，但這些認證不是您在 Visual Studio 內使用的認證或直接繫結至 Azure 帳戶的認證。
- 您想要在每次部署時刪除目標中的檔案。

## <a name="web-server-iis"></a>Web 伺服器 (IIS)

IIS 網頁伺服器可讓您將應用程式部署至 Azure 以外的 web 伺服器。 它可以部署到您擁有存取權的 IIS 伺服器 (網際網路或內部網路) ，包括其他雲端服務上的伺服器。 它可以搭配 Web Deploy 或 Web Deploy 套件使用。

選擇 IIS web 伺服器時，Visual Studio 會提示您輸入設定檔名稱，然後收集其他 **連接** 資訊，包括目標伺服器或位置、網站名稱和認證。 您可以在 [設定]**** 索引標籤上控制下列行為：

- 您想要部署的組態。
- 是否要從目的地中移除現有的檔案。
- 是否要在發行時預先編譯。
- 是否要將 [App_Data] 資料夾中的檔案從部署中排除。

您可以在 Visual Studio 中建立任意數目的 IIS web 伺服器部署設定檔，讓您可以使用不同的設定來管理設定檔。

### <a name="when-to-choose-web-server-iis-deployment"></a>選擇 web 伺服器 (IIS) 部署的時機

- 您要使用 IIS 來發佈可透過 Url 存取的網站或服務。
- 您想要使用認證進行部署，但這些認證不是您在 Visual Studio 內使用的認證或直接繫結至 Azure 帳戶的認證。
- 您想要在每次部署時刪除目標中的檔案。

如需詳細資訊，請參閱 [快速入門-部署至網站](quickstart-deploy-to-a-web-site.md)。 如需在 IIS 上進行 ASP.NET Core 疑難排解的詳細資訊，請參閱 [Azure App Service 和 iis 上的 ASP.NET Core 疑難排解](/aspnet/core/test/troubleshoot-azure-iis)。

## <a name="import-profile"></a>匯入設定檔

您可以在發佈至 IIS 或 Azure App Service 時匯入設定檔。 您可以使用*發佈設定檔*案 (* \* .publishsettings*) 來設定部署。 發行設定檔案是由 IIS 或 Azure App Service 所建立，或者可以手動方式建立，並可匯入至 Visual Studio 中。

使用發行設定檔案可以簡化部署設定，並在小組環境中更妥善地運作，而不是手動設定每個部署設定檔。

### <a name="when-to-choose-import-profile"></a>選擇匯入設定檔的時機

- 您正在發行至 IIS，並且想要簡化部署設定。
- 您要發行至 IIS 或 Azure App Service，並且想要加速部署設定以供重複使用，或讓團隊成員發行至相同的服務。

如需詳細資訊，請參閱下列：

- [匯入發佈設定並部署至 IIS](tutorial-import-publish-settings-iis.md)
- [匯入發行設定並部署至 Azure](tutorial-import-publish-settings-azure.md)

## <a name="next-steps"></a>後續步驟

教學課程：

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [將 ASP.NET core 應用程式發佈至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Visual C++ 中的部署](/cpp/windows/deployment-in-visual-cpp)
- [部署 UWP 應用程式](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [使用 Web Deploy 將 Node.js 應用程式發行至 Azure](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [將 Python 應用程式發佈到 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
