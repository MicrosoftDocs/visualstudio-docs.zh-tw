---
title: 使用實驗室環境進行開發
description: 瞭解實驗室環境，以及如何搭配 Azure Pipelines 或 Team Foundation Server 組建和發行來使用雲端。
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: how-to
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a16b8df2539272f96f0211fdf08e32fe4e4eaac8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887818"
---
# <a name="use-a-lab-environment-for-your-devops"></a>使用實驗室環境進行開發

實驗室環境是一個虛擬機器和實體電腦的集合，可用來開發和測試應用程式。 實驗室環境可以包含測試多層應用程式 (例如工作站、Web 伺服器和資料庫伺服器) 所需的多個角色。 此外，您可以使用建置-部署-測試工作流程搭配實驗室環境，將建置、部署和執行應用程式之自動化測試的流程自動化。

* **使用測試計劃執行自動化測試** − 您可以執行自動化測試的集合，稱為「測試計劃」，並檢視進度。

* **使用「建置、部署、測試」工作流程** − 您可以使用「建置、部署、測試」工作流程自動測試多層應用程式。 一般的範例是開始建置、將組建檔案部署到實驗室環境中的適當電腦，然後執行自動化測試的工作流程。 此外，您也可以排定以特定間隔執行工作流程。

* **收集所有電腦的診斷資料，即使是在手動測試期間** − 您可以同時收集多部電腦的診斷資料。 例如，在單次測試回合中，您可以從 Web 伺服器、資料庫伺服器以及用戶端，收集 IntelliTrace、測試影響，以及其他形式的資料。

以下是常見的實驗室環境拓撲的範例：

| 拓撲 | Description |
|---|---|
|![只有伺服器的拓撲](../media/topology_backend.png)| 此實驗室環境具有「伺服器拓撲」，這種拓撲經常用來在伺服器應用程式上執行手動測試，且允許測試者使用他們自己的用戶端電腦來確認環境中的 Bug。 在後端拓撲中，您的實驗室環境只包含伺服器。 當您使用這種拓撲類型時，通常會使用不屬於環境的用戶端電腦連接到實驗室環境中的伺服器。|
|![雲端實驗室環境](../media/topology_cloud.png)| 此實驗室環境提供與 _伺服器拓樸_ 類似的功能和特性，但移除在本機環境中執行實體或虛擬機器的需求，這樣可減少安裝時間、簡化維護工作，並將成本降至最低。 在 Microsoft Azure 這樣的雲端環境中，設定多個網站和虛擬機器，加上自訂的網路，快速且容易。|
|![用戶端實驗室環境](../media/topology_clientserver.png)| 此實驗室環境具有「用戶端伺服器拓撲」，這種拓撲經常用來測試有伺服器和用戶端元件的應用程式。 在用戶端/伺服器拓撲中，用來測試應用程式的所有用戶端和伺服器電腦都在您的實驗室環境中。 當您使用此拓撲時，可以從影響測試的每台電腦收集測試資料。|

:::row:::
    :::column:::
        ![影片的電影攝影機圖示](../../install/media/video-icon.png)
    :::column-end:::
    :::column:::
        [觀看影片](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) \(英文\) 了解如何管理實驗室環境以供測試之用。
    :::column-end:::
:::row-end:::

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>使用雲端搭配 Azure Pipelines 或 Team Foundation Server 的建置和發行

您可以使用 Team Foundation Server (TFS) 和 Azure Test Plans 的[建置和發行](/azure/devops/pipelines/index?view=vsts&preserve-view=true)功能，來執行自動化的測試及「建置 - 部署 - 測試」自動化。 其中一些優點包括：

* 您不需要組建控制器或測試控制器。
* 測試代理程式是透過工作，安裝為組建或版本的一部分。
* 自訂部署步驟很簡單。 您不必再受限於使用單一指令碼。 您也可以利用產品中可用的許多工作以及 Visual Studio Marketplace。
* 您不必維護測試套件。 您可以直接從二進位檔執行測試。
* 您在每個組建或版本中執行的測試，會獲得更豐富的內嵌報表體驗。
* 您可以追蹤每個環境目前已部署和測試的資產 (版本、組建、工作項目、認可)。
* 您可以自訂及擴充自動化功能，輕鬆部署多個測試環境，甚至部署生產環境。
* 您可以排程於簽入或認可時，或在每天的特定時間進行自動化。

如需詳細資訊，請參閱[使用建置或發行管理](use-build-or-rm-instead-of-lab-management.md)。

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>使用 Microsoft Test Manager 的 Visual Studio Lab Management 功能

當您使用 Visual Studio Enterprise Edition 時，可以使用 Microsoft Test Manager 的 Visual Studio Lab Management 功能來建立及管理實驗室環境。

Lab Management 會在您環境中的每部電腦上自動安裝測試代理程式。

如果您將 Lab Management 和 System Center Virtual Machine Manager (SCVMM) 搭配使用，則在使用實驗室環境時也會獲得下列益處：

* **快速重現電腦組態** − 您可以儲存虛擬機器的集合，這些虛擬機器已經過設定，可重建標準生產環境。 接著您可以在新的預存環境複本上執行每個測試回合。

* **重現 Bug 的確切條件** – 當測試回合失敗時，您可以儲存一份實驗室環境狀態的複本，並從建置結果或工作項目存取它。

* **同時執行多份實驗室環境複本** – 您可以同時執行多份實驗室環境複本，而不會有命名衝突。

### <a name="standard-environments-and-scvmm-environments"></a>標準環境與 SCVMM 環境

您可以用 Visual Studio Lab Management 建立兩個類型的實驗室環境：**標準環境** 和 **SCVMM 環境**。 然而，每個類型的環境有不同功能。

**標準環境：** 可包含虛擬與實體機器的混合。 您也可以將虛擬機器加入協力廠商虛擬架構所管理的標準環境。 另外，標準環境不需要 SCVMM 伺服器等其他伺服器資源。

**SCVMM 環境：** 只能包含由 SCVMM (System Center Virtual Machine Manager) 所管理的虛擬機器，因此 SCVMM 環境中的虛擬機器只能在 Hyper-V 虛擬架構上執行。 不過，SCVMM 環境提供標準環境中無法使用的下列自動化與管理功能：

- **環境快照：** 環境快照包含實驗室環境的狀態，因此您可以快速地還原乾淨的環境，或是儲存已修改過的環境狀態。 您也可以使用建置-部署-測試工作流程，將儲存和還原環境快照的流程自動化。

- **預存環境：** 您可以儲存一份 SCVMM 環境的複本，然後部署多份該環境的複本。

- **網路隔離：** 網路隔離允許您同時執行多份相同的 SCVMM 環境複本，而不會有電腦名稱衝突。

- **虛擬機器範本：** 虛擬機器範本是已移除其名稱及其他識別項的虛擬機器。 在 SCVMM 環境中部署 VM 範本時，Microsoft Test Manager 會產生新的識別項。 這允許您在相同環境或多個環境中部署多份虛擬機器的複本，然後同時執行虛擬機器。

- **預存虛擬機器：** 儲存在您的專案程式庫且包含唯一識別碼的虛擬機器。

> [!NOTE]
> Lab Management 不支援 SCVMM 2016。

如需 SCVMM 的相關資訊，請參閱 [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts&preserve-view=true)。

標準環境和 SCVMM 環境支援許多相同的功能。 但是有一些重大差異要考慮。 下表比較標準環境和 SCVMM 環境中可用的功能。

|功能|SCVMM 環境|標準環境|
|-|------------------------|-|
|**測試**|||
|執行手動測試|支援|支援|
|執行自動程式碼 UI 及其他自動化測試|支援|支援|
|使用診斷配接器提報大量 Bug|支援|支援|
|**建置部署**|||
|自動化建置-部署-測試工作流程|支援|支援|
|**環境建立和管理**|||
|使用實體機器和虛擬機器|不支援|支援|
|使用協力廠商虛擬機器|不支援|支援|
|自動將測試代理程式安裝到實驗室環境中的電腦|支援|支援|
|使用環境快照儲存和部署實驗室環境的狀態|支援|不支援|
|根據 VM 範本建立實驗室環境|支援|不支援|
|啟動/停止/快照環境|支援|不支援|
|使用 [環境檢視器] 連接到環境|支援|支援|
|使用網路隔離同時執行多個環境複本|支援|不支援|

### <a name="lab-management-concepts"></a>Lab Management 概念

以下是在您繼續之前應該熟悉的一些其他概念：

|詞彙|描述|
|-|-----------------|
|實驗室中心|建立和管理實驗室環境所在的 Microsoft Test Manager 區域。|
|Azure DevOps 專案實驗室|實驗室環境的集合已設定，讓您能連接到這些環境並執行它們的虛擬機器。|
|Azure DevOps 專案程式庫|預存虛擬機器、範本及預存實驗室環境的封存，已匯入您專案的主機群組中。 您可以將程式庫中的項目與 SCVMM 環境搭配使用，但無法直接將它們加入標準環境。 您無法執行程式庫中的項目，而是要使用它們來部署新的環境。|
|部署的環境|已部署到專案實驗室的實驗室環境，讓您能連線到此環境並執行其虛擬機器。|

如需 Lab Management 的詳細資訊，請參閱：

* [規劃您的實驗室](/previous-versions/ff756575(v=vs.140))
* [管理實驗室](/previous-versions/dd936084(v=vs.140))
* [設定 SCVMM 環境](/previous-versions/dd380687(v=vs.140))
* [管理權限](/previous-versions/dd380760(v=vs.140))
* [變更設定](/previous-versions/ee704508(v=vs.140))
* [疑難排解](/previous-versions/ee853230(v=vs.140))

如需設定環境的詳細資訊，請參閱：

* [建置和發行雲端環境](use-build-or-rm-instead-of-lab-management.md)
* [標準實驗室環境](/previous-versions/ee390842(v=vs.140))
* [SCVMM (虛擬) 環境](/previous-versions/ee943322(v=vs.140))
* [建立和使用網路隔離的環境](/previous-versions/ee518924(v=vs.140))
::: moniker-end

## <a name="see-also"></a>另請參閱

* [安裝和設定測試代理程式](../../test/lab-management/install-configure-test-agents.md)
* [Visual Studio Lab Management 指南](/archive/blogs/visualstudioalmrangers/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions)
* [Microsoft DevOps 部落格](https://devblogs.microsoft.com/devops/) \(英文\)