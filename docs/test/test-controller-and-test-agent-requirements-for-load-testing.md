---
title: " (負載測試的測試控制器/測試代理程式需求) "
description: 瞭解負載測試的測試控制器和測試代理程式需求。 Visual Studio 支援數種測試類型。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a123a147d038a41f799c2fdf9d4fb26eaa4f3490
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894487"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>負載測試的測試控制器和測試代理程式需求

許多測試類型 (包括單元、Web 效能、負載和手動測試) 都已經整合至 Visual Studio 中。 Visual Studio 可讓 Visual Studio 應用程式生命週期管理使用者使用測試控制器以及一或多個代理程式，在遠端電腦上執行測試。 請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>硬體和軟體需求

測試控制器和測試代理程式電腦都有特定的硬體和軟體需求。 此外，如果您想要跨多個語言部署測試控制器和測試代理程式電腦，就必須規劃如何支援這些語言。

### <a name="hardware-requirements"></a>硬體需求

下表顯示部署測試控制器和測試代理程式的建議硬體需求。

|**Configuration**|**元件**|**CPU**|**HD**|**記憶體**|
|-|-------------------|-|------------|-|
|少於 500 位虛擬使用者|測試代理程式|2.6 GHz|10 GB|2 GB|
|少於 1000 位虛擬使用者|測試代理程式|雙重處理器 2.6 GHz|10 GB|2 GB|
|N x 1000 位虛擬使用者|測試代理程式|延伸為 N 個代理程式，每個都具有雙重 2.6 Ghz|10GB|2GB|
|\< 30 部電腦於測試環境中。 這包括要測試的代理程式和伺服器。|測試控制器|2.6 GHz|||
|N x 30 部電腦於測試環境中。 這包括要測試的代理程式和伺服器。|測試控制器|N 2.6 GHz 處理器|||

> [!NOTE]
> 虛擬使用者的人數會隨著每個測試而大不相同。 造成這個變異的主要原因是「考慮時間」或使用者延遲的變異。 如需詳細資訊，請參閱[編輯考慮時間以模擬網站人類互動延遲](../test/edit-think-times-in-load-test-scenarios.md)。 在負載測試中，Web 測試一般都比單元測試更為有效，而且可產生更多的負載。 上表數字的有效情況：對一般 Web 應用程式執行 Web 測試時，搭配 3-5 秒的考慮時間。

這裡提供的方針可做為硬體規劃的一般指引。 測試資料的數量和測試代理程式的數目會使測試效能產生極大的差異。 對測試代理程式而言，CPU 速度和可用的記憶體將會限制測試負載。 此外，視測試代理程式的數目和測試的相關資料數量而定，測試控制器會需要更大量的資源。

執行 Visual Studio 的伺服器應該要有可靠的網路連線 (最小頻寬為 1 Mbps 而最大延遲時間為 350 毫秒)， 而且在測試代理程式和測試控制器之間不能有防火牆。 如果測試效能不符合您的期望，請考慮升級硬體組態。

### <a name="additional-hardware-considerations"></a>其他硬體考量

視測試持續期間和測試的大小而定，測試代理程式會在測試控制器上產生大量資料。 一般來說，您應該針對每 24 小時的測試資料，額外規劃 10 GB 的硬碟儲存區。

除了這裡所建議的硬體以外，您應該考慮為重要的伺服器加裝其他硬體設備，例如額外的電源供應器和風扇。

### <a name="language-requirements"></a>語言需求

為了避免混淆並簡化作業，測試控制器和測試代理程式應該設定為使用與電腦作業系統和 Team Foundation Server 一樣的語言。 如果測試代理程式和測試控制器是安裝在不同的電腦上，則兩者必須設定為使用相同的語言。 不過，您可以在英文版作業系統上安裝其他語言版本的 Visual Studio (只要該語言符合 Team Foundation Server 部署的語言即可)。

## <a name="monitor-agent-resources"></a>監視代理程式資源

您可以監視代理程式電腦來判定它們的資源需求，方法為觀察在測試期間執行和縮放的 *QTAgent\*.exe* 處理序。 *QTAgent\*.exe* 處理序上最常見的瓶頸為 CPU 使用率。 如果 CPU 使用率持續保持在九十幾，則表示代理程式的負載相當重。 次常見的瓶頸為記憶體使用量。 針對需求測試，監視這些資源有助於判定是否應增加電腦資源，或是以不同方式分散測試。

## <a name="see-also"></a>另請參閱

- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)
