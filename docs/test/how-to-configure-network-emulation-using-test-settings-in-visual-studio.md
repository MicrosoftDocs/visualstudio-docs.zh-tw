---
title: 使用測試設定來設定網路模擬
description: 瞭解如何設定診斷資料介面卡，以在 Visual Studio 的各種網路環境下測試您的應用程式。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 6126441890f34296fa0d8a9cda20bee32752cd81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966756"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>如何：在 Visual Studio 中使用測試設定來設定網路模擬

您可以設定診斷資料配接器，從 Visual Studio 測試不同網路環境下的應用程式。 當您執行測試時，也可以將其設定為測試人造網路負載或瓶頸。

> [!WARNING]
> 如果在實際網路上執行測試，實際網路與您模擬的網路相比較慢時，測試仍會以較慢的網路速度執行。 模擬也只會減慢網路環境速度，而不會加快速度。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
下列程序說明如何從組態編輯器設定網路模擬。 這些步驟同時適用於 Microsoft Test Manager 和 Visual Studio 中的組態編輯器。
::: moniker-end
::: moniker range=">=vs-2019"
下列程序說明如何從組態編輯器設定網路模擬。 這些步驟適用于 Visual Studio 中的設定編輯器。
::: moniker-end

> [!NOTE]
> 網路模擬診斷資料配接器僅適用於 Visual Studio 測試設定。 它不會用於 Microsoft Test Manager 中 (已在 Visual Studio 2017) 中淘汰的測試設定。

::: moniker range="vs-2017"
若要進行網路模擬，必須使用具備系統管理員權限的帳戶。 如果您為執行手動測試的本機角色選取了網路模擬，您就必須使用系統管理員權限啟動 Microsoft Test Manager。 如果您為其他任何角色選取了網路模擬，則您必須驗證該角色在電腦上的測試代理程式所使用的使用者帳戶是 [Administrators] 群組的成員。 如需如何設定測試代理程式帳戶的詳細資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。
::: moniker-end

> [!NOTE]
> Network Service 帳戶 (這是測試代理程式的預設帳戶) 並不是 [Administrators] 群組的成員。

**實際網路模擬**

Visual Studio 會針對所有測試類型使用軟體實際網路模擬。 其中包括負載測試。 實際網路模擬會藉由直接操作網路封包，來模擬網路狀況。 實際網路模擬器可以使用可靠的實體連結 (如乙太網路)，來同時模擬有線和無線網路。 下列網路屬性會納入實際網路模擬中：

- 網路的來回時間 (延遲)

- 可用的頻寬量

- 佇列行為

- 封包遺失

- 封包重新排序

- 錯誤傳用

實際網路模擬在根據 IP 位址或 TCP、UDP 和 ICMP 之類通訊協定來篩選網路封包上，也提供了相當的彈性。

網路架構開發人員和測試人員可以使用實際網路模擬，來模擬所要的測試環境、評定效能、預測變更的影響或者做出有關技術最佳化的決策。 與硬體測試平台相較之下，實際網路模擬是成本更低但彈性更高的一種解決方案。

## <a name="configure-network-emulation-for-your-test-settings"></a>設定測試設定的網路模擬

執行這個程序中的步驟之前，您必須先從 Visual Studio 開啟測試設定，然後選取 [資料和診斷] 頁面。

### <a name="to-configure-network-emulation-for-your-test-settings"></a>若要設定測試設定的網路模擬

1. 選取要用來模擬特定網路的角色。

    > [!NOTE]
    > 您只需在用戶端角色或伺服器角色上設定網路模擬配接器， 不需同時在兩個角色上使用該配接器。 這個配接器會模擬兩個角色之間通訊的網路雜訊，因此您不必在兩個角色上都加以使用。 除非必要，否則請選擇在用戶端角色上使用網路模擬配接器，以避免增加伺服器角色的負荷。

2. 選取 [網路模擬]，然後選擇 [設定]。

     如此即會顯示對話方塊以設定網路模擬。

3. 選擇 [選取要使用的網路設定檔] 旁的箭號，然後選取執行測試時要模擬的網路類型，例如 [Cable-DSL 768Kps]。

    > [!WARNING]
    > 如果在實際網路上執行測試，而實際網路比您模擬的網路慢時，測試仍會以較慢的網路速度執行。 模擬也只會減慢網路環境速度，而不會加快速度。

4. 如果您在測試設定中包含網路模擬診斷資料配接器，而且打算將它用於本機電腦，則也必須將網路模擬驅動程式繫結至電腦的其中一個網路介面卡。 網路模擬診斷資料配接器需要網路模擬驅動程式才能運作。 您可使用兩種方式來安裝網路模擬驅動程式並繫結至配接器：

    - **隨 Microsoft Visual Studio Test Agent 安裝的網路模擬驅動程式**：Microsoft Visual Studio Test Agent 可同時在遠端電腦和本機電腦上使用。 當您安裝 Visual Studio Test Agent 時，安裝程序包含的設定步驟會將網路模擬驅動程式繫結至網路介面卡。 如需詳細資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

    - **隨 Microsoft Visual Studio Test Professional 安裝的網路模擬驅動程式**：第一次使用網路模擬時，系統會提示您將網路模擬驅動程式繫結至網路介面卡。

    > [!TIP]
    > 不必安裝 Visual Studio 測試代理程式，也能在本機電腦上安裝網路模擬驅動程式，只要從命令列使用下列命令即可：**VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>另請參閱

- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)
- [執行手動測試 (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)
