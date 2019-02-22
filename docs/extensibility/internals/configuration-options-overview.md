---
title: 組態選項的概觀 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ce45aea2f39751822a3dda6f388bd2d8095775
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605090"
---
# <a name="configuration-options-overview"></a>組態選項概觀
中的專案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可支援多個可以建置、 偵錯、 執行，及/或已部署的組態。 組態是一組具名屬性、 通常編譯器參數和檔案位置的描述組建類型。 根據預設，新的方案包含兩個設定，*偵錯*並*發行*。 使用預設值，或修改以符合您特定的解決方案和/或專案需求，可以套用這些設定。 有些封裝可以建立兩種方式： 做為 ActiveX 編輯器，或為就地元件。 若要支援多個組態，但不需要專案。 如果沒有可用的只有一個組態，該組態會對應到所有的方案組態。

 組態通常包含兩個部分： 組態名稱 (例如*偵錯*或是*版本*) 與平台設定。 組態的平台名稱識別作業系統平台的組態的目標，例如 API 設定的環境。 使用者的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]無法建立平台，他們必須從選取項目選擇的專案，可讓 VSPackage。 當使用者安裝 VSPackage，建立的封裝開發期間傳遞平台可能會出現任何所需的平台名稱為基礎的封裝建立者所設定的任何條件。 然後，使用者可以選取從可透過 VSPackage 時的屬性頁會具現化的平台的清單。

 平台名稱是選擇性的因為並非所有的專案支援的平台概念。 設定當缺少平台名稱，該字串**n/A**會顯示在 UI 中。

 每個解決方案都有它自己組組態，其中只有一個可使用一次。 方案組態是一份不超過一個組態中每個專案。 「 超過 」 的規定是因為要排除的方案組態的專案選項。 使用者可以建立自己的自訂方案組態。

 下表說明專案的一般組態設定。 資料列會標示為 組態名稱與平台名稱的資料行。

|組態名稱|平台:Win32|平台:Win64|
|------------------------|----------------------|----------------------|
|*偵錯*|\<偵錯 Win32 設定 >|\<偵錯 Win64 設定 >|
|*發行*|\<發行 Win32 設定 >|\<發行 Win64 設定 >|
|*MyConfig*|N/A|\<MyConfig Win64 設定 >|

> [!NOTE]
>  您無法建立*MyConfig*排除 Win32 平台，除非您的目標專案的方案組態不支援 Win32。

 變更解決方案的作用中設定該方案中選取是建置、 執行、 偵錯，或部署的專案組態的設定。 比方說，如果您變更使用中的方案組態從*Release*要*偵錯*，該方案中的所有專案會自動都建置專案的組態所示方案的偵錯組態。 也稱為專案的組態*偵錯*除非使用者已手動變更環境的 Configuration Manager 中的流程範本。

 儲存每個專案的方案組態屬性包含專案名稱、 專案組態名稱、 旗標以指出可建立或部署，以及平台名稱。 如需詳細資訊，請參閱 <<c0> [ 方案組態](../../extensibility/internals/solution-configuration.md)。

 使用者可以檢視和選取的階層架構 (在 [方案總管] 中) 中的解決方案，並開啟屬性頁設定的解決方案組態參數。 同樣地，您可以檢視和設定方案總管 中選取專案，然後開啟該專案的屬性頁的專案組態參數。

 使用者也可以建置一個專案偵錯組態設定，如有必要使用發行組態設定與所有其餘部分。 如需詳細資訊，請參閱 <<c0> [ 建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)。

 下圖顯示如何實作介面，可支援方案和專案組態：

 ![組態介面圖形](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")組態介面

 上圖與相關的一些注意事項：

- `IDispatch` 標示為 選擇性組態物件中。 具體來說，是選擇性的以瀏覽物件上設定介面。

- `IVsDebuggableProjectCfg` 標示為在組態物件中，選擇性，但需要偵錯支援。

- `IVsProjectCfg2` 標示為在組態物件中，選擇性，但需要群組支援的輸出。

- 組態提供者物件標示為選擇性的物件，但選項是實作它的位置。 您可能會實作物件，或個別的物件上的 project 物件。

- `IVsCfgProvider2` 所需的支援平台和組態編輯。 `IVsCfgProvider` 就已足夠，如果您不會實作該功能。

- 其中某些物件顯示圖表中，為不同的物件可以結合到相同的類別，在可行的情況取決於您特定的設計需求。 在這一節的其他主題，不過，物件與這些物件相關聯的介面將會討論根據圖表中所示的案例。

- 某些物件會個別實作。 比方說，專案和方案建置會發生在個別的執行緒以及所要物件，描述組建組態分開管理組建生活物件中。

  如需有關的組態物件的介面和在上圖中的組態提供者物件介面的詳細資訊，請參閱[專案組態物件](../../extensibility/internals/project-configuration-object.md)。 颾魤 ㄛ[建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)提供有關組態產生器及組建相依性物件介面的詳細資訊並[來管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)進一步描述連接到組態部署器部署相依性物件的介面。 最後，[輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)描述輸出群組和輸出物件的介面，以及使用屬性頁面來檢視和設定組態相關的屬性。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [方案組態](../../extensibility/internals/solution-configuration.md)