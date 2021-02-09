---
title: 部署簡介
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8933127940cd8155bbf0854fd19c559022bceecb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912164"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Visual Studio 中的部署簡介

透過部署應用程式、服務或元件，就可以將它散發到其他電腦、裝置、伺服器或雲端上進行安裝。 請在 Visual Studio 中針對您需要的部署類型選擇適當的方法。  (許多應用程式類型都支援其他部署工具（例如命令列部署或 NuGet），但此處並未說明。 ) 

請參閱快速入門和教學課程，以取得逐步部署指示。 如需部署選項的概觀，請參閱[適合我的發行選項為何？](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)。

## <a name="deploy-to-a-local-folder"></a>部署到本機資料夾

部署至本機資料夾通常用於測試或開始預備部署，以使用另一個工具進行最終部署。

- **ASP.NET**、 **ASP.NET Core**、 **Node.js**、 **Python** 和。**NET Core**：使用 **發行** 工具部署至本機資料夾。 確切的可用選項取決於您的應用程式類型。 在 [方案總管] 中，在您的專案上按一下滑鼠右鍵，然後選取 [發佈]。  (如果您先前尚未設定任何發行設定檔，則必須選取 [ **建立新設定檔**]。 ) 下一步]，選取 [ **資料夾**]。 如需詳細資訊，請參閱[部署至本機資料夾](quickstart-deploy-to-local-folder.md)。

    ![顯示選取 [發佈] 的螢幕擷取畫面。](../deployment/media/quickstart-publish.png)

- **Windows 桌面**：您可以使用 ClickOnce 部署將 Windows 桌面應用程式發行至資料夾。 使用者只要按一下，就可以安裝應用程式。 如需詳細資訊，請參閱下列文章：

  - [使用 ClickOnce 部署 .NET Framework Windows 桌面應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。
  - [使用 ClickOnce 部署 .Net Windows 傳統型應用程式](quickstart-deploy-using-clickonce-folder.md)。
  - [使用 ClickOnce 部署 c + +/clr 應用程式](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ，或針對 c/c + + 使用，請參閱 [使用安裝專案部署原生應用程式](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)。

## <a name="publish-to-azure"></a>發佈至 Azure

- **ASP.NET**、 **ASP.NET Core**、 **Python** 和 **Node.js**：使用下列其中一種方法，發佈至 Azure App Service 或 Linux 上的 Azure App Service (使用容器) ：

  - 針對連續 (或自動) 部署應用程式，使用 Azure DevOps 與 [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)。
  - 針對一次 (或手動) 部署應用程式，請使用 Visual Studio 中的 [發行] 工具。

  針對提供更多自訂伺服器設定的部署，您也可以使用 **發佈** 工具將應用程式部署至 Azure 虛擬機器。

  若要使用 **發行** 工具，請以滑鼠右鍵按一下方案總管中的專案，然後選取 [ **發行**]。  (如果您先前已設定任何發行設定檔，則必須選取 [ **建立新設定檔**]。 ) 在 [ **發佈** ] 對話方塊中，選取 [ **App Service** ] 或 [ **Azure 虛擬機器**]，然後依照設定步驟進行。

  ![顯示選取 Azure App Service 的螢幕擷取畫面。](../deployment/media/quickstart-publish-azure-new.png "選擇 Azure App Service")

  從 Visual Studio 2017 版本15.7 開始，您可以將 ASP.NET Core 應用程式部署至 Linux 上的 App Service。

  針對 Python 應用程式，另請參閱 [Python - 發行至 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)。

  如需快速簡介，請參閱[發行至 Azure](quickstart-deploy-to-azure.md)及[發行至 Linux](quickstart-deploy-to-linux.md)。 此外，請參閱[將 ASP.NET Core 應用程式發行至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 如需使用 Git 進行部署，請參閱[使用 Git 將 ASP.NET Core 持續部署至 Azure](/aspnet/core/publishing/azure-continuous-deployment)。

  > [!NOTE]
  > 如果您還沒有 Azure 帳戶，可以在 [這裡註冊](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)。

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>發行至 web 或部署至網路共用

- **ASP.NET**、 **ASP.NET Core**、 **Node.js** 和 **Python**：您可以使用 [ **發佈** ] 工具，透過 FTP 或 Web Deploy 部署至網站。 如需詳細資訊，請參閱 [部署至網站](quickstart-deploy-to-a-web-site.md)。

    在方案總管中，以滑鼠右鍵按一下專案，然後選取 [ **發行**]。  (如果您先前已設定任何發行設定檔，則必須選取 [ **建立新設定檔**]。 ) 在 **發佈** 工具中，選取您要的選項，然後遵循設定步驟。

    ![顯示選取 IIS 的螢幕擷取畫面。](../deployment/media/quickstart-publish-iis.png)

    如需在 Visual Studio 中匯入發行設定檔的資訊，請參閱[匯入發行設定並部署至 IIS](../deployment/tutorial-import-publish-settings-iis.md)。

    您也可以使用許多其他方式來部署 ASP.NET 應用程式和服務。 如需詳細資訊，請參閱[部署 ASP.NET Web 應用程式和服務](/aspnet/overview/deployment)。

- **Windows 桌面**：您可以使用 ClickOnce 部署，將 Windows 桌面應用程式發行至 web 伺服器或網路檔案共用。 使用者只要按一下，就可以安裝應用程式。 如需詳細資訊，請參閱下列文章：

  - [使用 ClickOnce 部署 .NET Framework Windows 桌面應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [使用 ClickOnce 部署 .NET Windows 傳統型應用程式](quickstart-deploy-using-clickonce-folder.md)
  - [使用 ClickOnce 部署 c + +/CLR 應用程式](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>發行至 Microsoft Store

您可以從 Visual Studio 中建立應用程式套件，以部署至 Microsoft Store。

- **UWP**：您可以封裝您的應用程式，並使用功能表項目加以部署。 如需詳細資訊，請參閱[使用 Visual Studio 封裝 UWP 應用程式](/windows/uwp/packaging/packaging-uwp-apps)。

    ![顯示建立應用程式套件的螢幕擷取畫面。](../deployment/media/feature-tour-create-app-package.png)

- **Windows 桌面**：您可以使用從 Visual Studio 2017 15.4 版開始的傳統型橋接器部署至 Microsoft Store。 若要這樣做，請先建立 Windows 應用程式封裝專案。 如需詳細資訊，請參閱[為 Microsoft Store 封裝傳統型應用程式 (傳統型橋接器)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)。

    ![顯示選取 Windows 應用程式封裝專案的螢幕擷取畫面。](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>部署至裝置 (UWP)

如果您要部署 UWP 應用程式以在裝置上進行測試，請參閱 [Visual Studio 中的遠端電腦上執行 uwp 應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。

## <a name="create-an-installer-package-windows-desktop"></a>建立安裝程式套件 (Windows 桌面)

如果您需要比 ClickOnce 可以提供的桌面應用程式更複雜的安裝，您可以) 或自訂啟動載入器，建立 Windows Installer 套件 (MSI 或 EXE 安裝檔案。

- 您可以使用 [WiX 工具組 Visual Studio 2017 擴充](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)功能來建立 MSI 型安裝程式套件。 這是命令列工具組。
- 您可以使用 >flexera Software 的 [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) 來建立 MSI 或 EXE 安裝程式套件。 InstallShield 可搭配 Visual Studio 2017 和更新版本使用。 不支援社區版。

  > [!NOTE]
  > InstallShield 限量版不再隨附于 Visual Studio，Visual Studio 2017 和更新版本中則不支援。 請查看 [>flexera 軟體](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) 是否有未來的可用性。

- 您可以使用安裝專案 (vdproj) 來建立 MSI 或 EXE 安裝程式套件。 若要使用此選項，請安裝 [Visual Studio 安裝程式專案擴充功能](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview) \(英文\)。
- 您也可以藉由設定泛型安裝程式 (稱為啟動載入器) 來安裝傳統型應用程式的必要條件元件。 如需詳細資訊，請參閱 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)。

## <a name="deploy-to-a-test-lab"></a>部署至測試實驗室

透過將應用程式部署至虛擬環境，即可啟用更複雜的開發和測試。 如需詳細資訊，請參閱[在實驗室環境中測試](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)。

## <a name="continuous-deployment"></a>持續部署

您可以使用 Azure Pipelines 來啟用應用程式的持續部署。 如需詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) 及[部署至 Azure](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true)。

## <a name="deploy-a-sql-database"></a>部署 SQL 資料庫

- [變更目標平台和發行資料庫專案 (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [部署 Analysis Services 專案 (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [部署 Integration Services (SSIS) 專案和套件](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [建立並部署至本機資料庫](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>其他應用程式類型的部署

| 應用程式類型 | 部署案例 | 連結 |
| --- | --- | --- |
| **Office 應用程式** | 您可以從 Visual Studio 發行 Office 的增益集。 | [部署和發行 Office 增益集](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF 或 OData 服務** | 其他應用程式可以使用您部署至 Web 伺服器的 WCF RIA 服務。 | [開發和部署 WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | 從 Visual Studio 2017 開始就不再支援 LightSwitch，但仍然能夠從 Visual Studio 2015 和更早版本加以部署。 | [部署 LightSwitch 應用程式](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>下一步

在本教學課程中，您已快速瀏覽過不同應用程式的部署選項。

> [!div class="nextstepaction"]
> [適合我的發行選項為何？](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)