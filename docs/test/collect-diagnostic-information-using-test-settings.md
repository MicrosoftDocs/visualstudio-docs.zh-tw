---
title: 使用測試設定收集診斷資訊
description: 瞭解如何使用 Visual Studio 中的測試設定，在執行測試時收集額外的資料。 深入瞭解數個診斷資料配接器。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 564d1598dd4458a902df5cf0ddcae37afbf9c423
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868149"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>使用測試設定收集診斷資訊

您可以在 Visual Studio 中使用「測試設定」，在執行測試時收集額外的資料。 例如，您可能想要在執行測試時錄製視訊。 診斷資料配接器可用來：

- 收集文字格式的每個 UI 動作步驟

- 記錄每個 UI 動作以供播放之用

- 收集系統資訊

- 收集事件記錄檔資料

- 收集 IntelliTrace 資料，協助找出無法重現的 Bug

診斷資料配接器也可用來變更測試電腦的行為。 例如，透過 Visual Studio 中的測試設定就可以模擬各種不同的網路拓撲瓶頸，以評估小組應用程式的效能。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>使用 Visual Studio 的測試設定

若要使用 Visual Studio 執行您的單元測試、自動程式碼 UI 測試、Web 效能測試或負載測試，您可以加入、設定及選取要在執行測試時使用的測試設定。 若要從遠端執行測試、收集資料或影響測試電腦，您必須指定要在測試設定中使用的測試控制器。 測試控制器將具有可用於測試設定中每一個角色的代理程式。

## <a name="diagnostic-data-adapter-details"></a>診斷資料配接器詳細資料

下表提供可以將診斷資料配接器設定為搭配本機或遠端電腦角色使用之各種方式的概觀。

|測試設定中使用的診斷資料配接器|本機電腦的手動測試|自動化測試|手動測試：使用角色集合和環境收集資料|備註|
|-|-|-|-|-|
|**適用于 IntelliTrace 和測試影響的 ASP.NET 用戶端 Proxy：** 此 proxy 可讓您針對 IntelliTrace 和測試影響診斷資料配接器，收集從用戶端到 web 伺服器之 HTTP 呼叫的相關資訊。|是|是|是|-   僅當已針對用戶端角色選取 IntelliTrace 或測試影響診斷資料配接器時，才使用此項。|
|**ASP.NET profiler：** 您可以建立包含 ASP.NET 分析的測試設定，它會收集 ASP.NET web 應用程式的效能資料。|否|有 (請參閱備註)|否|-   只有當您從 Visual Studio 執行負載測試時，才支援這個診斷資料配接器。|
|**程式碼涵蓋範圍：** 您可以建立包含程式碼涵蓋範圍資訊的測試設定，用以調查測試所涵蓋的程式碼數量。|否|有 (請參閱備註)|否|-只有當您從 Visual Studio 或 *mstest.exe* 執行自動化測試，而且只能從執行測試的電腦執行自動化測試時，才可以使用程式碼涵蓋範圍。 不支援遠端集合。<br />-   如果您同時設定測試設定來收集 IntelliTrace 資訊，則無法收集程式碼涵蓋範圍資料。 **注意：** 這個診斷資料配接器僅適用於 Visual Studio 測試設定。 它不會用於 Microsoft Test Manager 中 (已在 Visual Studio 2017) 中淘汰的測試設定。 此外，這個配接器是為了提供與 Visual Studio 2010 測試專案的相容性。 **注意：** 為了提供相容性，當使用舊版 MSTest 執行器從 Microsoft Test Manager 或從 Visual Studio 的遠端測試代理程式執行自動化測試時，就會套用程式碼涵蓋範圍。|
|**事件記錄檔：** 您可以設定測試設定來包含事件記錄檔收集 (該事件記錄檔收集是包含在測試結果中)。|是|是|是||
|**IntelliTrace：** 您可以設定 *IntelliTrace* 的診斷資料配接器，以收集特定診斷追蹤資訊來協助找出難以重現的 Bug。 這樣就會建立包含這項資訊的 IntelliTrace 檔案。 IntelliTrace 檔案的副檔名為 *.iTrace*。 測試失敗時，您可以建立 Bug。 隨測試結果一起儲存的 IntelliTrace 檔會自動連結至此 Bug。 IntelliTrace 檔中收集的資料可縮短重現及診斷程式碼錯誤所需的時間，進而提高偵錯的效能。 使用這個 IntelliTrace 檔案，就可以在另一部電腦上模擬本機工作階段。 這樣可降低無法重現 Bug 的風險。|是|是|是|-   如果您啟用收集 IntelliTrace 資料的功能，則無法收集程式碼涵蓋範圍資料。<br />-   如果您針對 Web 用戶端角色使用 IntelliTrace，則必須同時針對 IntelliTrace 和測試影響診斷資料配接器選取 ASP.NET 用戶端 Proxy。<br />-   只支援下列 IIS 版本：IIS 7.0、IIS 7.5 和 IIS 8.0。|
|**網路模擬：** 您可以使用測試設定指定要對測試加上人為的網路負載。 網路模擬可藉由模擬特定網路連線速度 (如撥號連線)，對電腦的對外通訊產生影響。 |否|有 (請參閱備註)|否|您可以針對用戶端或伺服器角色使用網路模擬診斷資料配接器。 您不需要在彼此進行通訊的這兩個角色上使用配接器。 **注意：** 這個診斷資料配接器僅適用於 Visual Studio 測試設定。 它不會用於 Microsoft Test Manager 中 (已在 Visual Studio 2017) 中淘汰的測試設定。 **注意：** 網路模擬無法用以增加網路連線速度。 **警告：** 如果您在測試設定中包含網路模擬診斷資料配接器，而且打算將它用於本機電腦，則也必須將網路模擬驅動程式繫結至電腦的其中一個網路介面卡。 網路模擬診斷資料配接器需要網路模擬驅動程式才能運作。 您可使用兩種方式來安裝網路模擬驅動程式並繫結至配接器： <ul><li>**隨 Microsoft Visual Studio Test Agent 安裝的網路模擬驅動程式**：Visual Studio Test Agent 可同時在遠端電腦和本機電腦上使用。 當您安裝 Visual Studio Test Agent 時，安裝程序包含的設定步驟會將網路模擬驅動程式繫結至網路介面卡。 如需詳細資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。</li><li>**隨 Microsoft Visual Studio Test Professional 安裝的網路模擬驅動程式**：第一次使用網路模擬時，系統會提示您將網路模擬驅動程式繫結至網路介面卡。</li></ul> 不必安裝 Visual Studio Test Agent 也能在本機電腦上安裝網路模擬驅動程式，只要從命令列使用下列命令即可：**VSTestConfig NETWORKEMULATION /install** **警告：** 負載測試會忽略網路模擬配接器。 因為負載測試會改用負載測試情節的網路混合中指定的設定。|
|**系統資訊：** 測試設定可設定為包含測試執行所在電腦的相關系統資訊。|是|是|是||
|**測試影響：** 您可以收集在測試案例執行時，您的應用程式程式碼使用了哪些方法的相關資訊。 您可以將這項資訊對照開發人員對應用程式程式碼所做的變更，判斷有哪些測試受到這些開發變更的影響。|是|是|是|-   如果您收集 Web 用戶端角色的測試影響，則必須同時針對 IntelliTrace 和測試影響診斷資料配接器選取 ASP.NET 用戶端 Proxy。<br />-   只支援下列 IIS 版本：IIS 7.0、IIS 7.5 和 IIS 8.0。|
|**視訊錄製器：** 您可以在執行測試時，建立桌面工作階段的視訊錄製。 視訊可協助其他小組成員找出難以重現的應用程式問題。|是|有 (請參閱備註)|是|-   如果您啟用測試代理程式作為處理序而非服務執行，則可以在執行自動化測試時建立視訊錄製。|
