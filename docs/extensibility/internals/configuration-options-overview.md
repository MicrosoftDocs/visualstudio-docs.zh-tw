---
title: "組態選項的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f91f6c3668b7cc1ce881dd0b98d1bd5dddebf530
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="configuration-options-overview"></a>設定選項的概觀
中的專案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以支援多個可以建置、 偵錯、 執行，及/或已部署的組態。 組態是搭配命名集的屬性、 通常編譯器參數和檔案位置中所述的組建類型。 根據預設，新的方案包含兩個組態，偵錯和發行。 使用預設值，或修改以符合您特定的方案和/或專案需求，可以套用這些設定。 有些封裝可以建立兩種方式： 做為 ActiveX 編輯器，或為就地元件。 若要支援多個組態，但不需要專案。 如果使用只能在一個設定，該組態會對應到所有的方案組態。  
  
 組態通常包含兩個部分-平台設定與組態名稱 （例如偵錯或發行）。 組態的平台名稱識別作業系統平台的設定組態的目標，例如應用程式開發介面的環境。 使用者的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]無法建立平台; 它們必須從選取項目選擇 VSPackage 可讓一個專案。 當使用者安裝 VSPackage，建立的封裝開發期間傳遞平台就會出現任何所需的平台名稱為基礎的封裝建立者所設定的任何條件。 然後，使用者可以選取從屬性頁具現化時可供使用 VSPackage 透過平台清單。  
  
 平台名稱是選擇性的因為並非所有專案都支援的平台的概念。 當組態缺少平台名稱時，字串"n/A 」 會顯示在 UI 中。  
  
 每個解決方案都有它自己組組態，其中只有一個可以使用一次。 方案組態是一組中的每個專案只能有一個組態。 「 不多於 」 規定是因為專案中排除的方案組態選項。 使用者可以建立自己的自訂方案組態。  
  
 下表說明一般設定安裝專案。 資料列會標示為與組態名稱和資料行與平台名稱。  
  
|組態名稱|平台，Win32|平台 — Win64|  
|------------------------|----------------------|----------------------|  
|偵錯|\<偵錯 Win32 設定 >|\<偵錯 Win64 設定 >|  
|發行|\<釋放 Win32 設定 >|\<釋放 Win64 設定 >|  
|MyConfig|N/A|\<MyConfig Win64 設定 >|  
  
> [!NOTE]
>  您無法建立排除"Win32"平台，除非您的目標的專案不支援 Win32"MyConfig 」 的方案組態。  
  
 變更方案的作用中設定該方案中選取專案組態所建置、 執行、 偵錯或部署的集合。 例如，如果您從版本變更現用方案組態設為偵錯時，該方案中的所有專案會自動都建立的專案設定方案的偵錯組態所示。 專案的設定通常也是具名的偵錯除非使用者已手動變更環境的 Configuration Manager 中。  
  
 儲存每個專案的方案組態屬性包含專案名稱、 專案組態名稱、 旗標以指出以建置或部署，以及平台名稱。 如需詳細資訊，請參閱[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
 使用者可以檢視並選取階層 (位於 [方案總管]) 中的方案，並開啟屬性頁設定的方案組態參數。 同樣地，您可以檢視並設定專案組態參數在 [方案總管] 中選取專案並開啟該專案的屬性頁。  
  
 使用者也可以建立一個發行組態設定和所有其他使用與偵錯組態設定，如有必要的專案。 如需詳細資訊，請參閱[建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)。  
  
 下圖顯示如何實作的介面的支援方案與專案組態：  
  
 ![組態介面圖形](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
組態介面  
  
 上圖與相關的一些注意事項：  
  
-   `IDispatch`已標示為選擇性組態物件中。 尤其，它是選用組態介面來瀏覽物件上。  
  
-   `IVsDebuggableProjectCfg`標示為選擇性的組態物件，但需要偵錯支援。  
  
-   `IVsProjectCfg2`標示為選擇性的組態物件，但所需的群組支援的輸出。  
  
-   `Config Provider`物件標示為選擇性的物件，但是選項來實作它的位置。 您可以在專案物件或另一個物件上實作物件。  
  
-   `IVsCfgProvider2`所需的平台支援及編輯組態。 `IVsCfgProvider`已足夠，如果您要實作這項功能。  
  
-   其中某些物件顯示圖表中，為不同的物件可以結合到相同的類別，如果可行根據特定的設計需求。 在這一節的其他主題中，不過，物件與這些物件相關聯的介面將會討論根據圖表中所示的案例。  
  
-   某些物件會個別實作。 例如，專案和方案建置發生在不同的執行緒和物件描述的建置組態的物件分開管理組建生活。  
  
 組態物件的介面和在上圖中的組態提供者物件介面上的進一步資訊，請參閱[專案組態物件](../../extensibility/internals/project-configuration-object.md)。 此外，[建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)的組態產生器及建置相依性物件的介面，提供詳細資訊和[管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)進一步描述附加至的組態部署器和部署相依性物件的介面。 最後，[專案組態輸出](../../extensibility/internals/project-configuration-for-output.md)描述輸出群組和輸出物件的介面，並使用屬性頁，來檢視和設定組態相關的屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [建置專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)