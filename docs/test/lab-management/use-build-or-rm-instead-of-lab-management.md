---
title: "在 Visual Studio 中使用建置或發行管理進行自動化測試 | Microsoft Docs"
ms.date: 03/02/2018
ms.technology: vs-devops-test
ms.topic: article
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b12bffb6f2e5df0209fd3dfe3ea5fd005897d58d
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>使用 Build and Release Management 而非 Lab Management 進行自動化測試

如果您使用 Microsoft Test Manager (MTM) 和 Lab Management 進行自動化測試，或「建置、部署、測試自動化」，本主題會說明如何使用 Team Foundation Server (TFS) 和 Visual Studio Team Services (VSTS) 中的[建置和發行](/vsts/build-release/)功能，達到相同的目標。

## <a name="build-deploy-test-automation"></a>建置、部署、測試自動化

MTM 和 Lab Management 依賴 XAML 組建定義來自動化建置、部署和測試應用程式。 XAML 組建依賴各種以 MTM 建立的建構，例如實驗室環境、測試套件和測試設定，以及各種基礎結構元件，例如組建控制器、組建代理程式、測試控制器和測試代理程式，來達成這個目標。 使用 TFS 和 Team Services 的 Build or Release Management，可以較少的步驟完成相同的作業。

| 步驟 | 使用 XAML 組建 | 使用 Build or Release Management |
|-------|----------------------|-----------------|
| 找出要部署組建和執行測試的機器。 | 以 MTM 在這些機器上建立標準的實驗室環境。 | N/A |
| 找出要執行的測試。 | 以 MTM 建立測試套件、建立測試案例，以及建立自動化與每個測試案例的關聯性。 以可識別電腦角色的 MTM，在應該執行測試的實驗室環境中建立測試設定。 | 如果您計劃透過測試計劃來管理您的測試，請以相同的方式在 MTM 中建立自動化的測試套件。 或者，您也可以跳過此程序，如果您想要直接從組建產生的測試二進位檔執行測試。 不必每個案例都建立測試設定。 |
| 自動化部署及測試。 | 使用 LabDefaultTemplate.*.xaml 建立 XAML 組建定義。 在組建定義中指定組建、測試套件和實驗室環境。 | 建立單一環境的[建置或發行定義](/vsts/build-release/)。 使用命令列工作 (從 XAML 組建定義) 執行相同的部署指令碼，並使用 Test Agent 部署和執行功能測試工作執行自動化的測試。 指定機器清單及其認證，當作這些工作的輸入資料。 |

本案例使用 Build or Release Management 的優點包括：

* 您不需要組建控制器或測試控制器。
* 測試代理程式是透過工作，安裝為組建或版本的一部分。
* 自訂部署步驟很簡單。 您不必再受限於使用單一指令碼。 您也可以利用產品中可用的許多工作以及 Visual Studio Marketplace。
* 您不必維護測試套件。 您可以直接從二進位檔執行測試。
* 您在每個組建或版本中執行的測試，會獲得更豐富的內嵌報表體驗。
* 您可以追蹤每個環境目前已部署和測試的資產 (版本、組建、工作項目、認可)。
* 您可以自訂及擴充自動化功能，輕鬆部署多個測試環境，甚至部署生產環境。
* 您可以排程於簽入或認可時，或在每天的特定時間進行自動化。

## <a name="self-service-management-of-scvmm-environments"></a>SCVMM 環境的自助管理

[Microsoft Test Manager 的實驗室中心 ](https://msdn.microsoft.com/library/dd997438.aspx)支援使用 [SCVMM 伺服器](/system-center/vmm/overview?view=sc-vmm-1801)管理環境範本程式庫以及隨選佈建環境。

實驗室中心的自助服務佈建功能有兩個不同的目標：

* 提供更簡單的基礎結構管理方式。 管理 VM 和環境範本以及自動建立私人網路，以隔離曾是基礎結構管理範例的各環境複製品。

* 提供更簡單的方式，讓小組在其測試和部署活動中使用虛擬機器。 透過相同的 Team 專案安全性模型存取實驗室環境，且在這些測試案例中整合式使用虛擬機器，過去都是簡單取用的範例。

不過，隨著公用和私人雲端管理系統的巨大改變，如 [Microsoft Azure](https://azure.microsoft.com/) 和 [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/)，TFS 2017 和之後版本的基礎結構管理功能都不再變化。 而是將重點放在簡單取用透過此類雲端基礎結構永續管理的資源。

下表摘要說明您在實驗室中心執行的一般活動，以及如何透過 SCVMM 或 Azure (如果它們是基礎結構管理活動) 或透過 TFS 和 Team Services (如果它們是測試或部署活動) 完成它們：

| 步驟 | 使用實驗室中心 | 使用 Build or Release Management |
|-------|----------------------|-----------------|
| 管理環境範本程式庫。 | 建立實驗室環境。 在虛擬機器上安裝必要軟體。 將環境 Sysprep 和存放為程式庫範本。 | 直接使用 SCVMM 管理主控台來建立及管理虛擬機器範本或服務範本。 當使用 Azure 時，選取其中一個 [Azure 快速入門範本](/resources/templates/)。 |
| 建立實驗室環境。 | 選取並部署程式庫中的環境範本。 提供自訂虛擬機器設定的必要參數。 | 直接使用 SCVMM 管理主控台從範本建立 VM 或服務執行個體。 直接使用 Azure 入口網站建立資源。 或者，建立環境的版本定義。 使用 Azure 工作或 [SCVMM 整合延伸模組](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)的工作，建立新的虛擬機器。 建立此定義的新版本，相當於在實驗室中心建立新的環境。 |
| 連接到電腦。 | 在環境檢視器中開啟實驗室環境。 | 直接使用 SCVMM 管理主控台連線至虛擬機器。 或者，使用虛擬機器的 IP 位址或 DNS 名稱，開啟遠端桌面工作階段。 |
| 接受環境檢查點，或將環境還原到乾淨的檢查點。 | 在環境檢視器中開啟實驗室環境。 選取接受檢查點的選項，或還原到上一個檢查點。 | 直接使用 SCVMM 管理主控台，在虛擬機器上執行這些作業。 或者，將這些步驟執行為大型自動化過程的一部分，包括在版本定義中屬於環境的 [SCVMM 整合延伸模組](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)檢查點工作。 |

## <a name="creation-of-network-isolated-environments"></a>建立網路隔離環境

網路隔離的實驗室環境是可以安全複製，卻不會造成網路衝突的 SCVMM 虛擬機器群組。 在 MTM 中使用一連串指示即可完成這項作業：使用一組網路介面卡在私人網路中設定虛擬機器，然後用另一組網路介面卡在公用網路中設定虛擬機器。

但是，VSTS 和 TFS 搭配在 SCVMM 組建和部署工作，可用來管理 SCVMM 環境、佈建隔離的虛擬網路、以及實作建置-部署-測試案例。 例如，您可以使用此工作來：

* 建立、還原和刪除檢查點
* 使用範本來建立新的虛擬機器
* 啟動和停止虛擬機器
* 對 SCVMM 執行自訂 PowerShell 指令碼

如需詳細資訊，請參閱[建立虛擬網路隔離環境的建置-部署-測試案例](/vsts/build-release/actions/virtual-networks/create-virtual-network)。
