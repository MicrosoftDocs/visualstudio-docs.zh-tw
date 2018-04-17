---
title: 部署概觀-Visual Studio |Microsoft 文件
description: 深入了解您的選項，以部署應用程式，從 Visual Studio。
ms.custom: mvc
ms.date: 11/26/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ca458c0234de89fec814cfa5e639c13db9e6ca9b
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>快速入門： 第一次查看 Visual Studio 中的部署

透過部署應用程式、服務或元件，就可以將它散發到其他電腦、裝置、伺服器或雲端上進行安裝。 請在 Visual Studio 中針對您需要的部署類型選擇適當的方法。 （許多應用程式類型支援此處未描述其他部署工具命令列部署或 NuGet 等）。

如需逐步教學課程，請參閱。

### <a name="deploy-to-local-folder"></a>將部署到本機資料夾

- **ASP.NET**， **ASP.NET Core**， **Node.js**， **Python**，和**.NET Core**： 使用發行工具來部署至本機資料夾。 實際可用的選項取決於您的應用程式類型。 在 方案總管 中，以滑鼠右鍵按一下您的專案，然後選擇 **發行**，然後選擇 **資料夾**。 如需詳細資訊，請參閱[部署至本機資料夾](quickstart-deploy-to-local-folder.md)。

    ![選擇發行](../deployment/media/quickstart-publish.png)

- **Visual c + + 執行階段**： 您可以部署 Visual c + + 執行階段使用本機部署或靜態連結。 如需詳細資訊，請參閱[部署原生桌面應用程式 （Visual c + +）](/cpp/ide/deploying-native-desktop-applications-visual-cpp)。 

### <a name="publish-to-web-or-deploy-to-network-share"></a>發行至 Web 或網路共用部署

- **ASP.NET**， **ASP.NET Core**， **Node.js**， **Python**，和**.NET Core**： 您可以將部署到使用發行工具使用 FTP 或 Web Deploy 的網站。 如需詳細資訊，請參閱[部署網站至](quickstart-deploy-to-a-web-site.md)。

    在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。 在 [發行] 工具中，選擇您想要的選項組態步驟。

    ![選擇 IIS、 FTP 和其他內容。](../deployment/media/quickstart-publish-iis-ftp.png)

    您也可以部署 ASP.NET 應用程式和服務中的其他方法的數字。 如需詳細資訊，請參閱[部署 ASP.NET web 應用程式和服務](http://www.asp.net/aspnet/overview/deployment)。

- **Visual c + + 執行階段**： 您可以部署 Visual c + + 執行階段使用集中部署。 如需詳細資訊，請參閱[部署原生桌面應用程式 （Visual c + +）](/cpp/ide/deploying-native-desktop-applications-visual-cpp)。 

- **Windows 桌面**可以發行到 web 伺服器或網路檔案共用使用 ClickOnce 部署的 Windows 桌面應用程式。 使用者只要按一下，就可以安裝應用程式。 如需詳細資訊，請參閱[部署桌面應用程式使用 ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)和[部署原生應用程式使用 ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)。

### <a name="publish-to-azure"></a>發佈至 Azure

- **ASP.NET、 ASP.NET Core、 Python、 Node.js 和.NET Core** web 應用程式： 您可以使用 [發行] 工具，快速地將應用程式部署至 Azure App Service 或至 Azure 虛擬機器。 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。 在 發行 對話方塊中，選擇  **Microsoft Azure App Service**或**Microsoft Azure 虛擬機器**，然後依照 設定步驟。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-azure.png "選擇 Azure App Service")

    若要發行至 Azure 虛擬機器，向右捲動並選取**Microsoft Azure 虛擬機器**。

    快速簡介，請參閱[發行到 Azure](quickstart-deploy-to-azure.md)。 此外，請參閱[ASP.NET Core 應用程式發行至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 使用 Git 的部署，請參閱[的 ASP.NET Core 使用 Git 連續部署](/aspnet/core/publishing/azure-continuous-deployment)。

    > [!NOTE]
    > 如果您沒有 Azure 帳戶，您可以[這裡進行註冊](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)。

- 其他**Azure 服務**： 請參閱特定[Azure 服務](/azure/#pivot=products)可能支援的 Visual Studio 的不同的部署選項的文件。

### <a name="publish-to-microsoft-store"></a>發行至 Microsoft Store

從 Visual Studio 中，您可以建立以部署至 Microsoft Store 的應用程式套件。

- **UWP**： 您可以封裝應用程式並部署使用功能表項目。 如需詳細資訊，請參閱[UWP 應用程式封裝使用 Visual Studio](/windows/uwp/packaging/packaging-uwp-apps)。

    ![建立應用程式套件](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows 桌面**： 您可以部署到 Microsoft Store 使用桌面橋接器在 Visual Studio 2017 版本 15.4 中啟動。 若要這樣做，請開始建立 Windows 應用程式封裝專案。 如需詳細資訊，請參閱[桌面應用程式封裝 Microsoft Store (桌面 Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)。

    ![桌面的橋接器](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>建立安裝程式套件 （Windows 用戶端）

- 您可以使用建立 MSI 為基礎的 WiX 安裝程式[WiX 工具組 Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera 軟體可搭配使用 Visual Studio 2017 （不支援的 Community 版本）。 請注意 InstallShield Limited Edition 不再隨附於 Visual Studio 和 Visual Studio 2017; 不支援請洽詢[Flexera 軟體](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)有關未來的可用性。

- 如果您想要建立安裝專案 (vdproj)，安裝[Visual Studio 2017 Installer Projects extension](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)。

- 您可以藉由設定泛型安裝程式，稱為啟動載入器安裝桌面應用程式的必要條件元件。 如需詳細資訊，請參閱[應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)。

### <a name="deploy-to-test-lab"></a>若要測試實驗室部署

您可以啟用更趨精密完美的開發和測試部署到虛擬環境的應用程式。 如需詳細資訊，請參閱[在實驗室環境測試](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)。

### <a name="devops-deployment"></a>DevOps 部署

在小組環境中，您可以使用 Visual Studio Team Services (VSTS) 以啟用您的應用程式的連續部署。 如需詳細資訊，請參閱[組建與版本](/vsts/build-release/index)和[部署至 Azure](/vsts/deploy-azure/index)。

### <a name="deployment-for-other-app-types"></a>部署其他應用程式類型

| 應用程式類型 | 部署情節 | 連結 |
| --- | --- | --- |
| **Office 應用程式** | 您可以從 Visual Studio 的 office 發行增益集。 | [部署及發行 Office 增益集](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF 或 OData 服務**  | 其他應用程式可以使用您部署至 web 伺服器的 WCF RIA 服務。 | [開發和部署 WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch 已不再支援在 Visual Studio 2017，但仍然從 Visual Studio 2015 及更早版本可以部署。 | [部署 LightSwitch 應用程式](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

