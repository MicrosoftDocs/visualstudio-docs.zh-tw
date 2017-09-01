---
title: "使用 Build or Release Management 進行自動化測試 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automated testing, lab management, test lab
ms.assetid: F34B0D19-B430-4C01-B402-62A861007E71
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 77a0339e1aae3036990f0d9d133a1fcb68844486
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>使用 Build and Release Management 而非 Lab Management 進行自動化測試

如果您使用 Microsoft Test Manager (MTM) 和 Lab Management 進行自動化測試，或「建置、部署、測試自動化」，本主題會說明如何使用 Team Foundation Server (TFS) 和 Visual Studio Team Services 中的[組建 &amp; 版本](https://www.visualstudio.com/team-services/continuous-integration/)功能，達到相同的目標：

* [建置、部署、測試自動化](#bdtautomation)

* [SCVMM 環境的自助管理](#managescvmm)

Build and Release Management 不支援自助服務建立網路隔離的 SCVMM 環境，而且沒有計劃在未來提供這項支援。 但有一些[建議的替代項目](#isolatedenvir)。

<a name="bdtautomation"></a>
## <a name="build-deploy-test-automation"></a>建置、部署、測試自動化

MTM 和 Lab Management 依賴 XAML 組建定義來自動化建置、部署和測試應用程式。
XAML 組建依賴各種以 MTM 建立的建構，例如實驗室環境、測試套件和測試設定，以及各種基礎結構元件，例如組建控制器、組建代理程式、測試控制器和測試代理程式，來達成這個目標。 使用 TFS 和 Team Services 的 Build or Release Management，可以較少的步驟完成相同的作業。

| 步驟 | 使用 XAML 組建 | 使用 Build or Release Management |
|-------|----------------------|-----------------|
| 找出要部署組建和執行測試的機器。 | 以 MTM 在這些機器上建立標準的實驗室環境。 | N/A |
| 找出要執行的測試。 | 以 MTM 建立測試套件、建立測試案例，以及建立自動化與每個測試案例的關聯性。 以可識別電腦角色的 MTM，在應該執行測試的實驗室環境中建立測試設定。 | 如果您計劃透過測試計劃來管理您的測試，請以相同的方式在 MTM 中建立自動化的測試套件。 或者，您也可以跳過此程序，如果您想要直接從組建產生的測試二進位檔執行測試。 不必每個案例都建立測試設定。 |
| 自動化部署及測試。 | 使用 LabDefaultTemplate.*.xaml 建立 XAML 組建定義。 在組建定義中指定組建、測試套件和實驗室環境。 | 建立單一環境的[組建或版本定義](https://www.visualstudio.com/team-services/continuous-integration/)。 使用命令列工作 (從 XAML 組建定義) 執行相同的部署指令碼，並使用 Test Agent 部署和執行功能測試工作執行自動化的測試。 指定機器清單及其認證，當作這些工作的輸入資料。 |

本案例使用 Build or Release Management 的優點包括：

* 您不需要組建控制器或測試控制器。
* 測試代理程式是透過工作，安裝為組建或版本的一部分。
* 自訂部署步驟很簡單。 您不必再受限於使用單一指令碼。 您也可以利用產品中可用的許多工作以及 Visual Studio Marketplace。
* 您不必維護測試套件。 您可以直接從二進位檔執行測試。
* 您在每個組建或版本中執行的測試，會獲得更豐富的內嵌報表體驗。
* 您可以追蹤每個環境目前已部署和測試的資產 (版本、組建、工作項目、認可)。
* 您可以自訂及擴充自動化功能，輕鬆部署多個測試環境，甚至部署生產環境。
* 您可以排程於簽入或認可時，或在每天的特定時間進行自動化。

<a name="managescvmm"></a>
## <a name="self-service-management-of-scvmm-environments"></a>SCVMM 環境的自助管理

[Microsoft Test Manager 的實驗室中心 ](https://msdn.microsoft.com/library/dd997438.aspx)支援使用 [SCVMM 伺服器](https://technet.microsoft.com/system-center-docs/vmm/vmm)管理環境範本程式庫以及隨選佈建環境。

實驗室中心的自助服務佈建功能有兩個不同的目標：

* 提供更簡單的基礎結構管理方式。 管理 VM 和環境範本以及自動建立私人網路，以隔離曾是基礎結構管理範例的各環境複製品。

* 提供更簡單的方式，讓小組在其測試和部署活動中使用虛擬機器。 透過相同的 Team 專案安全性模型存取實驗室環境，且在這些測試案例中整合式使用虛擬機器，過去都是簡單取用的範例。

不過，隨著公用和私人雲端管理系統的巨大改變，如 [Microsoft Azure](https://azure.microsoft.com/) 和 [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/)，TFS 2017 和之後版本的基礎結構管理功能都不再變化。 而是將重點放在簡單取用透過此類雲端基礎結構永續管理的資源。

下表摘要說明您習慣在實驗室中心執行的一般活動，以及如何透過 SCVMM 或 Azure (如果它們是基礎結構管理活動) 或透過 TFS 和 Team Services (如果它們是測試或部署活動) 完成它們：

| 步驟 | 使用實驗室中心 | 使用 Build or Release Management |
|-------|----------------------|-----------------|
| 管理環境範本程式庫。 | 建立實驗室環境。 在虛擬機器上安裝必要軟體。 將環境 Sysprep 和存放為程式庫範本。 | 直接使用 SCVMM 管理主控台來建立及管理虛擬機器範本或服務範本。 使用 Azure 時，從 [Azure Marketplace](https://azure.microsoft.com/marketplace/) 或從 [Azure 快速入門範本](https://azure.microsoft.com/documentation/templates/) 選取其中一個預先定義的 [Azure 資源管理員範本](https://azure.microsoft.com/documentation/templates/)。 |
| 建立實驗室環境。 | 選取並部署程式庫中的環境範本。 提供自訂虛擬機器設定的必要參數。 | 直接使用 SCVMM 管理主控台從範本建立 VM 或服務執行個體。 直接使用 Azure 入口網站建立資源。 或者，建立環境的版本定義。 使用 Azure 工作或 [SCVMM 整合延伸模組](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)的工作，建立新的虛擬機器。 建立此定義的新版本，相當於在實驗室中心建立新的環境。 |
| 連接到電腦。 | 在環境檢視器中開啟實驗室環境。 | 直接使用 SCVMM 管理主控台連線至虛擬機器。 或者，使用虛擬機器的 IP 位址或 DNS 名稱，開啟遠端桌面工作階段。 |
| 接受環境檢查點，或將環境還原到乾淨的檢查點。 | 在環境檢視器中開啟實驗室環境。 選取接受檢查點的選項，或還原到上一個檢查點。 | 直接使用 SCVMM 管理主控台，在虛擬機器上執行這些作業。 或者，將這些步驟執行為大型自動化過程的一部分，包括在版本定義中屬於環境的 [SCVMM 整合延伸模組](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)檢查點工作。 |

<a name="isolatedenvir"></a>
## <a name="self-service-creation-of-network-isolated-environments"></a>自助建立網路隔離環境

網路隔離的實驗室環境是可以安全複製，卻不會造成網路衝突的 SCVMM 虛擬機器群組。 在 MTM 中使用一連串指示即可完成這項作業：使用一組網路介面卡在私人網路中設定虛擬機器，然後用另一組網路介面卡在公用網路中設定虛擬機器。

隨著公用和私人雲端管理系統的巨大改變，如 [Microsoft Azure](https://azure.microsoft.com/) 和 [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/)，您可以放心直接依賴有類似功能的雲端管理工具。 Build and Release Management 中沒有對等方法可完成此目標。

如果需要網路隔離，歡迎您多加考慮下列的替代方案：

* 隔離網路的動機之一，曾是容易設定的多個複製品。 因為每個複製品都確實是和原版完全一樣的複本，所以電腦名稱和組態設定會保留原狀，這讓設定新環境變得更容易。 不過，相同的優點在稍後的生命週期 (例如，生產環境) 中也引起了很多問題，因為最後部署應用程式的方式不相同。 所以，請**改為**考慮以設定生產環境的相同方式設定新環境，避免使用網路隔離。

* 請針對您的測試需求使用公用雲端基礎結構，如 [Microsoft Azure](https://azure.microsoft.com/)。 您可以輕鬆使用[Azure Resource Manager 範本](https://azure.microsoft.com/documentation/templates/)，從 [Azure Marketplace](https://azure.microsoft.com/marketplace/) 或從 [Azure 快速入門範本](https://azure.microsoft.com/documentation/templates/)設定透過私人網路連線的虛擬機器群組，並只使用 Proxy 或 'jumpbox' 公開至公用網路。

