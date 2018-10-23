---
title: 部署功能導覽
description: 深入了解部署從 Visual Studio 的應用程式的選項。
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83b6449d3f9fb41280d9e0b051c5baf3edbf5a66
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320549"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>快速入門： 初步了解在 Visual Studio 中的部署

藉由部署的應用程式、 服務或元件，您將散發它安裝在其他電腦、 裝置或伺服器，或在雲端中。 請在 Visual Studio 中針對您需要的部署類型選擇適當的方法。 （許多應用程式類型支援此處未描述其他部署工具命令列部署或 NuGet 等）。

請參閱快速入門和教學課程逐步部署指示。 如需部署選項的概觀，請參閱 <<c0> [ 哪些發佈選項適合我？](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)。

## <a name="deploy-to-local-folder"></a> 部署到本機資料夾

部署至本機資料夾通常用來進行測試，或若要開始另一個工具用於最終部署階段式的部署。

- **ASP.NET**， **ASP.NET Core**， **Node.js**， **Python**，並。**NET Core**： 使用發行工具來部署到本機資料夾。 確切的可用選項取決於您的應用程式類型。 在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選擇**發佈**。 (如果您先前已設定任何發行設定檔，您必須按一下**建立新的設定檔**。)接下來，選擇**資料夾**。 如需詳細資訊，請參閱 <<c0> [ 部署至本機資料夾](quickstart-deploy-to-local-folder.md)。

    ![選擇發行](../deployment/media/quickstart-publish.png)

- **Visual c + + 執行階段**： 您可以部署 Visual c + + 執行階段使用本機部署或靜態連結。 如需詳細資訊，請參閱 <<c0> [ 部署原生桌面應用程式 （Visual c + +）](/cpp/ide/deploying-native-desktop-applications-visual-cpp)。

## <a name="publish-to-azure"></a>發佈至 Azure

- **ASP.NET**， **ASP.NET Core**， **Python**，和**Node.js**： 您可以使用發行工具，快速將應用程式部署至 Azure App Service 或 Azure 虛擬機器。 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。 (如果您先前已設定任何發行設定檔，您必須按一下**建立新的設定檔**。)在 發行 對話方塊中，選擇**App Service**或是**Azure 虛擬機器**，然後依照 設定步驟。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-azure.png "選擇 Azure App Service")

    在 Visual Studio 2017 15.7 版及更新版本，您可以部署到 ASP.NET Core 應用程式**適用於 Linux 的 App Service**。

    針對 Python 應用程式，另請參閱[Python-發佈至 Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)。

    如需快速簡介，請參閱 <<c0> [ 發佈至 Azure](quickstart-deploy-to-azure.md)並[發佈至 Linux](quickstart-deploy-to-linux.md)。 此外，請參閱[將 ASP.NET Core 應用程式發佈至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 使用 Git 進行部署，請參閱 <<c0> [ 持續部署至 Azure Git 的 ASP.NET Core 的](/aspnet/core/publishing/azure-continuous-deployment)。

    如需有關從 Azure App Service 的發行設定檔匯入至 Visual Studio，請參閱[匯入發佈設定，並部署至 Azure](../deployment/tutorial-import-publish-settings-azure.md)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您可以[在這裡註冊](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)。

## <a name="publish-to-web-or-deploy-to-network-share"></a>發佈至網路或網路共用部署

- **ASP.NET**， **ASP.NET Core**， **Node.js**，和**Python**： 您可以使用發行工具來部署至網站，使用 FTP 或 Web Deploy。 如需詳細資訊，請參閱 <<c0> [ 部署至網站](quickstart-deploy-to-a-web-site.md)。

    在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。 (如果您先前已設定任何發行設定檔，您必須按一下**建立新的設定檔**。)在 [發行] 工具中，選擇您想要的選項依照組態步驟。

    ![IIS、 FTP 等選擇。](../deployment/media/quickstart-publish-iis-ftp.png)

    如需匯入發行設定檔在 Visual Studio 中的資訊，請參閱 <<c0> [ 匯入發佈設定和部署至 IIS](../deployment/tutorial-import-publish-settings-iis.md)。

    您也可以部署 ASP.NET 應用程式和許多其他方式的服務。 如需詳細資訊，請參閱 <<c0> [ 部署 ASP.NET web 應用程式和服務](http://www.asp.net/aspnet/overview/deployment)。

- **Visual c + + 執行階段**： 您可以部署使用集中部署 Visual c + + 執行階段。 如需詳細資訊，請參閱 <<c0> [ 部署原生桌面應用程式 （Visual c + +）](/cpp/ide/deploying-native-desktop-applications-visual-cpp)。

- **Windows 桌面**您可以發行至 web 伺服器或網路檔案共用使用 ClickOnce 部署的 Windows 桌面應用程式。 使用者只要按一下，就可以安裝應用程式。 如需詳細資訊，請參閱 <<c0> [ 部署桌面應用程式使用 ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)並[部署原生應用程式使用 ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)。

## <a name="publish-to-microsoft-store"></a>發行至 Microsoft Store

從 Visual Studio 中，您可以建立以部署至 Microsoft Store 應用程式套件。

- **UWP**： 您可以封裝您的應用程式，並使用功能表項目進行部署。 如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio 封裝 UWP 應用程式](/windows/uwp/packaging/packaging-uwp-apps)。

    ![建立應用程式套件](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows 桌面**： 您可以部署到使用傳統型橋接器開始在 Visual Studio 2017 15.4 版 Microsoft Store。 若要這樣做，請先建立 Windows 應用程式封裝專案。 如需詳細資訊，請參閱 <<c0> [ 為 Microsoft Store （傳統型橋接器） 封裝傳統型應用程式](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)。

    ![桌面橋接器](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>部署至裝置 (UWP)

如果您要部署 UWP 應用程式在裝置上進行測試，請參閱[在 Visual Studio 中的遠端電腦上執行 UWP app](../debugger/run-windows-store-apps-on-a-remote-machine.md)。

## <a name="create-an-installer-package-windows-client"></a>建立安裝程式套件 （Windows 用戶端）

如果 「 您需要更複雜的安裝的桌面應用程式會比[ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)可以提供，您可以建立的安裝程式套件，安裝專案中或自訂啟動載入器。

- 以 MSI 為基礎的 WiX 安裝程式可以使用來建立[WiX 工具組 Visual Studio 2017 擴充功能](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera Software 從可搭配 Visual Studio 2017 (Community Edition 不支援)。 請注意，InstallShield Limited Edition 不再隨附於 Visual Studio，而且不支援在 Visual Studio 2017;洽詢[Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)有關未來的可用性。

- 如果您想要建立安裝專案 (vdproj)，安裝[Visual Studio 2017 安裝程式專案延伸模組](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)。

- 您可以藉由設定泛型安裝程式，也就是啟動載入器安裝必要元件，針對桌面應用程式。 如需詳細資訊，請參閱 <<c0> [ 應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)。

## <a name="deploy-to-test-lab"></a>若要測試實驗室部署

您可以啟用更複雜的開發和部署您的應用程式至虛擬環境進行測試。 如需詳細資訊，請參閱 <<c0> [ 測試實驗室環境](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)。

## <a name="devops-deployment"></a>DevOps 部署

在小組環境中，您可以使用 Azure Pipelines，以啟用您應用程式的持續部署。如需詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) 與[部署到 Azure](/azure/devops/deploy-azure/index?view=vsts)。

## <a name="deployment-for-other-app-types"></a>部署其他應用程式類型

| 應用程式類型 | 部署情節 | 連結 |
| --- | --- | --- |
| **Office 應用程式** | 您可以從 Visual Studio 發行 Office 增益集。 | [部署及發行 Office 增益集](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF 或 OData 服務**  | 其他應用程式可以使用您部署至 web 伺服器的 WCF RIA 服務。 | [開發及部署 WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch 在 Visual Studio 2017 已不再支援，但仍可以從 Visual Studio 2015 和更早版本部署。 | [部署 LightSwitch 應用程式](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>後續步驟

在此教學課程中，您快速看了不同應用程式的部署選項。

> [!div class="nextstepaction"]
> [哪些發佈選項適合我？](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
