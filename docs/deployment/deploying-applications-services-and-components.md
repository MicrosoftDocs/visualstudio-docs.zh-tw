---
title: 部署功能導覽
description: 了解從 Visual Studio 部署應用程式的選項。
ms.custom: mvc
ms.date: 01/29/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dab79e4cbc9ab9b37a9052ee1337a5e9b94a6947
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742452"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Visual Studio 中的部署簡介

透過部署應用程式、服務或元件，就可以將它散發到其他電腦、裝置、伺服器或雲端上進行安裝。 請在 Visual Studio 中針對您需要的部署類型選擇適當的方法。 (許多應用程式類型支援此處未描述的其他部署工具，例如命令列部署或 NuGet 等)。

請參閱快速入門和教學課程以取得逐步部署指示。 如需部署選項的概觀，請參閱[適合我的發行選項為何？](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)。

## <a name="deploy-to-local-folder"></a>部署至本機資料夾

部署至本機資料夾通常用於測試，或是用來開始使用另一個工具進行最終部署的分段部署。

- **ASP.NET**、**ASP.NET Core**、**Node.js**、**Python** 及 .**NET Core**：使用發行工具部署至本機資料夾。 確切的可用選項取決於您的應用程式類型。 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (如果您之前已設定任何發行設定檔，則必須按一下 [建立新設定檔])。接下來，選擇 [資料夾]。 如需詳細資訊，請參閱[部署至本機資料夾](quickstart-deploy-to-local-folder.md)。

    ![選擇 [發行]](../deployment/media/quickstart-publish.png)

- **Windows 傳統型**：使用 ClickOnce 部署可以將 Windows 傳統型應用程式發行至資料夾。 使用者只要按一下，就可以安裝應用程式。 如需詳細資訊，請參閱[使用 ClickOnce 部署傳統型應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# 和 Visual Basic)。 針對 C++/CLR，請參閱[使用 ClickOnce 部署原生應用程式](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)，針對 C/C++，請參閱[使用安裝專案部署原生應用程式](/cpp/ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)。

## <a name="publish-to-azure"></a>發佈至 Azure

- **ASP.NET**、**ASP.NET Core**、**Python** 及 **Node.js**：使用下列其中一個方法發行至 Azure App Service 或 Azure App Service Linux (使用容器)。

  - 針對連續 (或自動) 部署應用程式，使用 Azure DevOps 與 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops)。

  - 針對一次 (或手動) 部署應用程式，請使用 Visual Studio 中的 [發行] 工具。

  針對提供伺服器自訂組態的部署，您也可以使用 [發行] 工具將應用程式部署至 Azure 虛擬機器。

  若要使用 [發行] 工具，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [發行]。 (如果您之前已設定任何發行設定檔，則必須按一下 [建立新設定檔])。在 [發行] 對話方塊中，選擇 [App Service] 或 [Azure 虛擬機器]，然後遵循設定步驟。

  ![選擇 [Azure App Service]](../deployment/media/quickstart-publish-azure.png "選擇 [Azure App Service]")

  從 Visual Studio 2017 15.7 版開始，您可以將 ASP.NET Core 應用程式部署至**適用於 Linux 的 App Service**。

  針對 Python 應用程式，另請參閱 [Python - 發行至 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)。

  如需快速簡介，請參閱[發行至 Azure](quickstart-deploy-to-azure.md)及[發行至 Linux](quickstart-deploy-to-linux.md)。 此外，請參閱[將 ASP.NET Core 應用程式發行至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 如需使用 Git 進行部署，請參閱[使用 Git 將 ASP.NET Core 持續部署至 Azure](/aspnet/core/publishing/azure-continuous-deployment)。

  如需將發行設定檔從 Azure App Service 匯入至 Visual Studio 的資訊，請參閱[匯入發行設定並部署至 Azure](../deployment/tutorial-import-publish-settings-azure.md)。

  > [!NOTE]
  > 如果您還沒有 Azure 帳戶，則可以[在這裡註冊](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)。

## <a name="publish-to-web-or-deploy-to-network-share"></a>發行至 Web 或部署至網路共用

- **ASP.NET**、**ASP.NET Core**、**Node.js** 及 **Python**：您可以使用發行工具，來利用 FTP 或 Web Deploy 部署至網站。 如需詳細資訊，請參閱[部署至網站](quickstart-deploy-to-a-web-site.md)。

    在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。 (如果您之前已設定任何發行設定檔，則必須按一下 [建立新設定檔])。在發行工具中，選擇您想要的選項並遵循設定步驟。

    ![選擇 [IIS、FTP 等等]。](../deployment/media/quickstart-publish-iis-ftp.png)

    如需在 Visual Studio 中匯入發行設定檔的資訊，請參閱[匯入發行設定並部署至 IIS](../deployment/tutorial-import-publish-settings-iis.md)。

    您也可以使用許多其他方式來部署 ASP.NET 應用程式和服務。 如需詳細資訊，請參閱[部署 ASP.NET Web 應用程式和服務](http://www.asp.net/aspnet/overview/deployment)。

- **Windows 傳統型**：使用 ClickOnce 部署可以將 Windows 傳統型應用程式發行至 Web 伺服器或網路檔案共用。 使用者只要按一下，就可以安裝應用程式。 如需詳細資訊，請參閱[使用 ClickOnce 部署傳統型應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# 和 Visual Basic)。 針對 C++/CLR，請參閱[使用 ClickOnce 部署原生應用程式](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)，針對 C/C++，請參閱[使用安裝專案部署原生應用程式](/cpp/ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)。

## <a name="publish-to-microsoft-store"></a>發行至 Microsoft Store

您可以從 Visual Studio 中建立應用程式套件，以部署至 Microsoft Store。

- **UWP**：您可以封裝應用程式，並使用功能表項目加以部署。 如需詳細資訊，請參閱[使用 Visual Studio 封裝 UWP 應用程式](/windows/uwp/packaging/packaging-uwp-apps)。

    ![建立應用程式套件](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows 桌面**：從 Visual Studio 2017 15.4 版開始，您可以使用傳統型橋接器部署至 Microsoft Store。 若要這樣做，請先建立 Windows 應用程式封裝專案。 如需詳細資訊，請參閱[為 Microsoft Store 封裝傳統型應用程式 (傳統型橋接器)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)。

    ![傳統型橋接器](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>部署至裝置 (UWP)

如果您要部署 UWP 應用程式以便在裝置上進行測試，請參閱[在 Visual Studio 的遠端電腦上執行 UWP 應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。

## <a name="create-an-installer-package-windows-desktop"></a>建立安裝程式套件 (Windows 桌面)

如果您需要比 [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) 可提供的傳統型應用程式更複雜的安裝，您可以建立 Windows Installer 套件 (MSI 或 EXE 安裝檔案) 或自訂啟動載入器。

- MSI 型安裝程式套件可以使用 [WiX 工具組 Visual Studio 2017 延伸模組](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)來建立。 這是命令列工具組。

- 可以使用 Flexera Software 的 [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) 來建立 MSI 或 EXE 安裝程式套件。 InstallShield 可以與 Visual Studio 2017 (不支援 Community Edition) 搭配使用。 請注意，InstallShield Limited Edition 不再隨附於 Visual Studio，且 Visual Studio 2017 不支援該版本；請洽詢 [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) 以了解未來的供應狀況。

- 可以使用安裝專案 (vdproj) 建立 MSI 或 EXE 安裝程式套件。 若要使用此選項，請安裝 [Visual Studio 2017 安裝程式專案延伸模組](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)。

- 您也可以藉由設定泛型安裝程式 (稱為啟動載入器) 來安裝傳統型應用程式的必要條件元件。 如需詳細資訊，請參閱[應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)。

## <a name="deploy-to-test-lab"></a>部署至測試實驗室

透過將應用程式部署至虛擬環境，即可啟用更複雜的開發和測試。 如需詳細資訊，請參閱[在實驗室環境中測試](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)。

## <a name="continuous-deployment"></a>連續部署

您可以使用 Azure Pipelines 來啟用應用程式的持續部署。 如需詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) 及[部署至 Azure](/azure/devops/deploy-azure/index?view=vsts)。

## <a name="deployment-for-other-app-types"></a>其他應用程式類型的部署

| 應用程式類型 | 部署情節 | 連結 |
| --- | --- | --- |
| **Office 應用程式** | 您可以從 Visual Studio 發行 Office 的增益集。 | [部署和發行 Office 增益集](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF 或 OData 服務** | 其他應用程式可以使用您部署至 Web 伺服器的 WCF RIA 服務。 | [開發和部署 WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | Visual Studio 2017 中不再支援 LightSwitch，但仍然能夠從 Visual Studio 2015 和更早版本加以部署。 | [部署 LightSwitch 應用程式](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已快速瀏覽過不同應用程式的部署選項。

> [!div class="nextstepaction"]
> [適合我的發行選項為何？](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
