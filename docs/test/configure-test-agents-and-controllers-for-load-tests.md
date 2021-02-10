---
title: 設定負載測試的測試代理程式/測試控制器
description: 瞭解 Visual Studio 如何使用實體或虛擬機器建立模擬負載，以產生比單一電腦可單獨產生更多的負載。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 50356044b4463353f99ddf93ac41e08a572f3879
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957240"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>用於執行負載測試的測試代理程式和測試控制器概觀

Visual Studio 可以使用實體或虛擬機器產生應用程式適用的模擬負載。 這些機器必須設為單一測試控制器和一個或多個測試代理程式。 測試控制器和測試代理程式可以用來產生單一電腦無法產生的多個負載。

> [!NOTE]
> 您也可以使用雲端式負載測試提供虛擬機器，產生多位使用者同時存取網站之負載。 但是，不支援在雲端託管的虛擬機器上使用測試控制器/測試代理程式設定。 如需雲端式負載測試的詳細資訊，請參閱 [使用 Azure Test Plans 執行負載測試](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>負載模擬架構

負載模擬架構是由 Visual Studio 用戶端、測試控制器和測試代理程式所組成。

- 用戶端用來開發測試、執行測試以及檢視測試結果。

- 測試控制器用來管理測試代理程式和收集測試結果。

- 測試代理程式用來執行測試和收集資料 (包括系統資訊以及在測試設定中定義的 ASP.NET 分析資料)。

此架構提供下列優點：

- 藉由新增其他測試代理程式至測試控制器來產生更多負載的能力。

- 在同一部電腦或不同電腦上安裝用戶端、測試控制器和測試代理程式軟體的彈性。 例如：

   **本機組態：**

  - 電腦 1： Visual Studio、控制器、代理程式。

    ![使用控制器和代理程式的本機電腦](./media/load-test-configa.png)

    **一般遠端組態：**

  - 電腦 1 和 2：Visual Studio (多位測試人員可以使用同一個控制器)。

  - 電腦 3：控制器 (也可以安裝代理程式)。

  - 電腦 4-n：所有與電腦 3 的控制器相關聯的代理程式。

    ![使用控制器和代理程式的遠端電腦](./media/load-test-configb.png)

雖然測試控制器通常能管理數個測試代理程式，但是一個代理程式只能與單一控制器相關聯。 每個測試代理程式可由一組開發人員共用。 這個架構能讓您輕鬆地增加代理程式的數量，進而產生更大的負載。

## <a name="test-agent-and-test-controller-interaction"></a>測試代理程式和測試控制器互動

測試控制器會管理一組測試代理程式以執行測試。 測試控制器藉由與測試代理程式之間的溝通，即可啟動測試、停止測試、追蹤測試代理程式狀態，以及收集測試結果。

### <a name="test-controller"></a>測試控制器

測試控制器提供用來執行測試的一般架構，並包含執行負載測試的特殊功能。 測試控制器會將負載測試傳送到所有的測試代理程式，並等待所有測試代理程式將測試初始化。 當所有測試代理程式皆準備就緒時，測試控制器會傳送訊息至測試代理程式以啟動測試。

### <a name="test-agent"></a>測試代理程式

測試代理程式會以做為服務的方式執行，接聽來自測試控制器的要求以啟動新的測試。 當測試代理程式收到要求時，測試代理程式服務會啟動執行測試所在的處理序。 每個測試代理程式都會執行相同的負載測試。

測試代理程式由系統管理員指派權重，並根據測試代理程式的加權來分散負載。 例如，如果測試代理程式 1 的加權是 30，測試代理程式 2 的加權是 70，負載設定為 1000 位使用者，那麼測試代理程式 1 會模擬 300 位虛擬使用者，而測試代理程式 2 會模擬 700 位虛擬使用者。 請參閱[使用 Visual Studio 管理測試控制器和測試代理程式](../test/manage-test-controllers-and-test-agents.md)。

測試代理程式會以一組測試和一組模擬參數做為輸入。 重要概念是測試與執行測試所在的電腦並無關聯。

## <a name="test-controller-and-test-agent-connection-points"></a>測試控制器和測試代理程式連接點

下圖顯示測試控制器、測試代理程式與用戶端之間的連接點。 本文將概述哪些通訊埠會用於連入和連出連線，以及這些通訊埠所使用的安全性限制。

![測試控制器和測試代理程式的通訊埠與安全性](./media/test-controller-agent-firewall.png)

如需詳細資訊，請參閱[設定測試控制器和測試代理程式的連接埠](../test/configure-ports-for-test-controllers-and-test-agents.md)。

## <a name="test-controller-and-agent-installation-information"></a>測試控制器和代理程式安裝資訊

如需測試控制器和測試代理程式的軟硬體需求、安裝程序以及針對最佳效能進行環境設定等的重要資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>使用測試控制器和測試代理程式與單元測試

安裝測試控制器和一個或多個代理程式後，您可以在負載測試的測試設定中指定是否使用測試控制器進行遠端執行。 此外，您還可以在測試設定中指定與代理程式關聯的角色能使用的資料和診斷配接器。

## <a name="see-also"></a>另請參閱

- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)
