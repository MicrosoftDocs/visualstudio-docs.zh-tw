---
title: 適用於 Python 的 Azure 雲端服務專案範本
description: Visual Studio 提供以 Python 所撰寫適用於 Azure 雲端服務的範本，其中包括角色部署、相依性和疑難排解。
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 2de0f255da54d5bd8abf865f6534041d88bbbca3
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254832"
---
# <a name="azure-cloud-service-projects-for-python"></a>適用於 Python 的 Azure 雲端服務專案

Visual Studio 提供的範本有助您使用 Python 以開始建立 Azure 雲端服務。

[雲端服務](/azure/cloud-services/)是由任意數目的「背景工作角色」和「Web 角色」所組成，它們會分別執行不同概念的工作，但可以視需求跨虛擬機器分別進行複寫來做出調整。 Web 角色提供前端 Web 應用程式的裝載。 在 Python 的考慮下，任何支援 WSGI 的 web 架構都可用來撰寫 () [Web 專案範本](python-web-application-project-templates.md) 所支援的應用程式。 背景工作角色適用於長時間執行，且不會直接與使用者互動的程序。 它們通常會使用隨一起安裝的「azure」套件內的套件 [`pip install azure`](https://pypi.org/project/azure) 。

本文包含 Visual Studio 2017 及更新版本中專案範本和其他支援 (與舊版類似，但有一些差異) 的詳細資料。 如需搭配 Python 使用 Azure 的詳細資訊，請瀏覽 [Azure Python 開發人員中心](/azure/python/)。

## <a name="create-a-project"></a>建立專案

1. 安裝 [適用于 Visual Studio 的 Azure .NET SDK](https://visualstudio.microsoft.com/vs/azure-tools/)，這是使用雲端服務範本的必要項。
1. 在 Visual Studio 中，**選取**  >  [檔案 **新**  >  **專案**]，然後搜尋「azure Python」，並從清單中選取 **Azure 雲端服務**：

    ![適用於 Python 的 Azure 雲端專案範本](media/template-azure-cloud-project.png)

1. 選取要包含的一或多個角色。 雲端專案可以結合以不同語言撰寫的角色，因此您可以輕鬆地以最適合的語言撰寫應用程式的每個部分。 若要在完成此對話方塊後將新角色新增至專案，請以滑鼠右鍵按一下 **方案總管** 中的 [**角色**]，然後選取 [**加入**] 下的其中一個專案。

    ![在 Azure 雲端專案範本中新增角色](media/template-azure-cloud-service-project-wizard.png)

1. 建立個別角色專案後，如果您選取的角色使用其他的 Python 封裝 (例如 Django、Bottle 或 Flask 架構)，系統會提示您安裝它們。

1. 將新角色新增至專案後，就會出現組態指示。 通常不需要進行組態變更，但未來自訂專案時可能十分有用。 請注意，同時新增多個角色時，只會針對最後一個角色的指示維持開啟。 不過，您可以在其他角色個別的 *readme.mht* 檔案 (位於角色的根目錄或 *bin* 資料夾中) 中找到指示和疑難排解祕訣。

1. 專案的 *bin* 資料夾也包含一或兩個用來設定虛擬機器的 PowerShell 指令碼，包括安裝 Python、專案中的任何 [*requirements.txt*](#dependencies) 檔案，以及設定 IIS (如有需要)。 您可以視需要針對部署編輯這些檔案，但您能以其他方式管理最常見的選項 (請參閱下面的[設定角色部署](#configure-role-deployment))。 不建議您移除這些檔案，因為如果無法使用這些檔案，系統會改用舊版的設定指令碼。

    ![背景工作角色支援檔案](media/template-azure-cloud-service-worker-role-support-files.png)

    若要將這些設定腳本新增至新的專案，請以滑鼠右鍵按一下專案、選取 [**加入**  >  **新專案**]，然後選取 [ **Web 角色支援** 檔案] 或 [背景 **工作角色支援** 檔案]。

## <a name="configure-role-deployment"></a>設定角色部署

角色專案 *bin* 資料夾中的 PowerShell 指令碼，可控制該角色的部署，並可以編輯以自訂設定：

- *ConfigureCloudService.ps1* 用於 Web 和背景工作角色，通常用來安裝並設定相依性，以及設定 Python 版本。
- *LaunchWorker.ps1* 僅用於背景工作角色，可用來變更啟始行為、新增命令列引數，或是新增環境變數。

這兩個檔案都包含自訂的指示。 您也可以將另一項工作新增至主要雲端服務專案的 *ServiceDefinition.csdef* 檔案，將 `PYTHON` 變數設定為其已安裝 *python.exe* (或對等項目) 的路徑，來安裝自己的 Python 版本。 設定 `PYTHON` 時，不會從 NuGet 安裝 Python。

其他的設定可依下列方式完成：

1. 透過更新您專案根目錄中的 *requirements.txt* 檔案，來使用 `pip` 安裝套件。 *ConfigureCloudService.ps1* 指令碼會將此檔案安裝在部署上。
1. 修改 *web.config* 檔案 (Web 角色) 或 *ServiceDefinition.csdef* 檔案的 `Runtime` 區段 (背景工作角色) 來設定環境變數。
1. 修改 *ServiceDefinitions.csdef* 檔案的 `Runtime/EntryPoint` 區段中的命令列，來指定用於背景工作角色的指令碼和引數。
1. 透過 *web.config* 檔案設定 Web 角色的主要控制代碼指令碼。

## <a name="test-role-deployment"></a>測試角色部署

撰寫角色時，您可以使用雲端服務模擬器在本機上測試雲端專案。 該模擬器隨附於 Azure SDK 工具，而且是您的雲端服務發行至 Azure 時使用之環境的精簡版本。

若要啟動模擬器，請先確定您的雲端專案在方案中是啟始專案，方法是以滑鼠右鍵按一下並選取 [設定為啟始專案]。 然後選取 [ **debug**  >  **開始調試**] (**F5**) 或 [啟動時不 **進行調試]**  >   (**Ctrl** + **F5**) 。

請注意，由於模擬器的限制，您將無法針對 Python 程式碼進行偵錯。 因此建議您獨立地執行角色來對角色進行偵錯，然後在發佈前使用模擬器進行整合測試。

## <a name="deploy-a-role"></a>部署角色

若要開啟 [發佈] 精靈，請在 [方案總管] 中選取角色專案，然後從主功能表選取 [建置] > [發佈]，或是以滑鼠右鍵按一下專案並選取 [發佈]。

發佈程序牽涉到兩個階段。 首先，Visual Studio 會建立包含雲端服務之所有角色的單一封裝。 此套件是要部署至 Azure 的項目，它會為每個角色初始化一或多部虛擬機器並部署來源。

當每部虛擬機器啟動時，它會執行 *ConfigureCloudService.ps1* 指令碼並安裝任何相依性。 此指令碼預設會從 [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) 安裝 Python 的最新版本，以及 *requirements.txt* 檔案中指定的所有套件。

最後，背景工作角色會執行 *LaunchWorker.ps1*，這會開始執行您的 Python 指令碼；Web 角色會初始化 IIS 並開始處理 Web 要求。

## <a name="dependencies"></a>相依性

針對雲端服務，*ConfigureCloudService.ps1* 指令碼會使用 `pip` 來安裝一組 Python 相依性。 相依性應該在名為 *requirements.txt* 的檔案中指定(可透過修改 *ConfigureCloudService.ps1* 來自訂)。 該檔案在初始化過程中會使用 `pip install -r requirements.txt` 來執行。

請注意，雲端服務執行個體不包括 C 編譯器，因此含有 C 延伸模組的所有程式庫都必須提供預先編譯的二進位檔。

PIP 與其相依性，以及 *requirements.txt* 中的所有套件都會自動下載，且可能會被視為需付費的頻寬使用量。 請參閱 [管理必要套件](managing-required-packages-with-requirements-txt.md)，以取得管理 *requirements.txt* 檔案的詳細資料。

## <a name="troubleshooting"></a>疑難排解

如果您的 Web 或背景工作角色在部署後無法正確運作，請檢查下列各項：

- 您的 Python 專案包含 (至少) 的 *bin \\* 資料夾：

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (適用於背景工作角色)
  - *ps.cmd*

- 您的 Python 專案包含列出所有相依性的 *requirements.txt* 檔案 (或是一組 wheel 檔案集合)。
- 在雲端服務上啟用遠端桌面，並調查記錄檔。
- *ConfigureCloudService.ps1* 與 *LaunchWorker.ps1* 的記錄檔是儲存在遠端電腦的 *C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles* 資料夾上。
- Web 角色會將額外的記錄檔寫入至 *web.config* 設定的路徑，也就是 `WSGI_LOG` appSetting 中的路徑。 大部分的一般 IIS 或 FastCGI 記錄也適用。
- 目前，*LaunchWorker.ps1.log* 檔案是檢視 Python 背景工作角色所顯示之輸出或錯誤的唯一方式。
