---
title: 設定選項概述 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709416"
---
# <a name="configuration-options-overview"></a>設定選項概述
中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案可以支援可生成、除錯、執行和/或部署的多個配置。 配置是使用一組命名屬性(通常是編譯器開關和檔案位置)描述的生成類型。 預設情況下,新解決方案包含兩個配置:*除錯*與*發佈*。 這些配置可以使用其預設設置應用,也可以修改以滿足您的特定解決方案和/或專案要求。 某些包可以通過兩種方式構建:作為 ActiveX 編輯器或作為就地元件。 但是,專案不需要支援多個配置。 如果只有一個配置可用,則該配置將映射到所有解決方案配置中。

 配置通常由兩部分組成:配置名稱(如*調試*或*發佈*)和平臺設置。 配置的平台名稱識別配置目標的環境,如 API 集或作業系統平臺。 使用者不能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]創建平臺;他們必須從專案 VSPackage 允許的選擇中進行選擇。 當使用者安裝 VSPackage 時,在程式包開發期間創建的交付平臺可以基於包建立者設置的任何條件顯示所需的任何平臺名稱。 然後,用戶可以在實例化屬性頁時,從通過 VSPackage 提供的平臺清單中選擇。

 平臺名稱是可選的,因為並非所有專案都支援平臺的概念。 當設定缺少平台名稱時,字串**N/A**將顯示在 UI 中。

 每個解決方案都有自己的配置集,其中只有一個一個可以一次處於活動狀態。 解決方案配置是每個項目中不超過一個配置的一組。 "不超過"規定是由於可以選擇將專案從解決方案配置中排除。 用戶可以創建自己的自定義解決方案配置。

 下表說明了專案的典型配置設置。 行用配置名稱和帶有平臺名稱的列標記。

|組態名稱|平台: Win32|平臺: Win64|
|------------------------|----------------------|----------------------|
|*偵錯*|\<除錯 win32 設定>|\<除錯 Win64 設定>|
|*釋放*|\<發佈 Win32 設置>|\<發佈 Win64 設置>|
|*我的康菲克*|N/A|\<MyConfig Win64 設定>|

> [!NOTE]
> 除非您定位的專案不支援 Win32,否則您無法建立排除 Win32 平臺的*MyConfig*解決方案配置。

 更改解決方案的活動配置將選擇在該解決方案中生成、運行、調試或部署的專案配置集。 例如,如果將活動解決方案配置從 *「發布」* 更改為 *「除錯*」,則該解決方案中的所有專案都將自動使用解決方案的調試配置中指示的專案配置生成。 除非使用者已在環境的設定管理器中進行了手動更改,否則項目的設定也命名為*除錯*。

 為每個專案存儲的解決方案配置屬性包括專案名稱、專案配置名稱、指示是生成還是部署的標誌以及平臺名稱。 有關詳細資訊,請參考[解決方案設定](../../extensibility/internals/solution-configuration.md)。

 使用者可以透過在層次結構(解決方案資源管理員)中選擇解決方案並打開屬性頁來查看和設置解決方案配置參數。 同樣,您可以通過在解決方案資源管理器中選擇專案並打開該專案的屬性頁來查看和設置專案配置參數。

 如有必要,使用者還可以使用發佈配置設置構建一個專案,其餘專案使用調試配置設置。 有關詳細資訊,請參閱[用於建構的項目設定](../../extensibility/internals/project-configuration-for-building.md)。

 下圖顯示了如何實現支援解決方案和專案配置的介面:

 ![設定介面圖形](../../extensibility/internals/media/vsconfiginterfaces.gif "vs 設定介面")設定介面

 與上圖有關的幾條註釋:

- `IDispatch`在配置物件中標記為可選。 具體而言,在流覽物件上具有配置介面是可選的。

- `IVsDebuggableProjectCfg`在配置物件中標記為可選,但調試支援是必需的。

- `IVsProjectCfg2`在配置物件中標記為可選,但需要輸出分組支援。

- Config 提供程式物件被標記為可選物件,但選項是實現它的位置。 您可以在項目物件或單獨物件上實現該物件。

- `IVsCfgProvider2`平臺支援和配置編輯需要。 `IVsCfgProvider`如果不實現該功能,就足夠了。

- 關係圖中顯示的一些物件作為單獨的物件可以合併到同一類中,其中根據您的特定設計要求具有實用性。 但是,在本節中的其他主題中,將根據關係圖中提供的方案討論與這些對象關聯的對象和介面。

- 某些對像是單獨實現的。 例如,專案和解決方案構建發生在單獨的線程上,用於管理生成生活的物件與描述生成配置的物件分開。

  有關上一個設定物件介面和設定提供程式物件介面的詳細資訊,請參考 Project[設定物件](../../extensibility/internals/project-configuration-object.md)。 此外,[用於建構的專案配置](../../extensibility/internals/project-configuration-for-building.md)提供有關配置產生器和生成依賴項物件介面的詳細資訊,[用於管理部署的專案配置](../../extensibility/internals/project-configuration-for-managing-deployment.md)進一步描述了附加到配置部署者和部署依賴項物件的介面。 最後,[輸出的專案配置](../../extensibility/internals/project-configuration-for-output.md)描述了輸出組和輸出物件介面,以及使用屬性頁來查看和設置與配置相關的屬性。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [編譯的項目設定](../../extensibility/internals/project-configuration-for-building.md)
- [解決方案配置](../../extensibility/internals/solution-configuration.md)
