---
title: 設定選項總覽 |Microsoft Docs
description: 瞭解 Visual Studio 中專案設定的選項。 「設定」（configuration）是一種以命名屬性集和檔案位置所描述的組建類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad30e3f7b91e8a76715f66d9f6701597f3830bd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057126"
---
# <a name="configuration-options-overview"></a>設定選項總覽
中的專案 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可支援多個可建立、調試、執行和/或部署的設定。 「設定」（configuration）是一種以命名屬性集（通常是編譯器參數和檔案位置）描述的組建類型。 根據預設，新解決方案包含兩個設定： *Debug* 和 *Release*。 您可以使用預設設定來套用這些設定，或修改這些設定以符合您的特定解決方案及/或專案需求。 某些封裝可以用兩種方式來建立：作為 ActiveX 編輯器或就地元件。 不過，專案不需要支援多個設定。 如果只有一個可用的設定，則該設定會對應到所有解決方案設定。

 設定通常是由兩個部分所組成：設定名稱 (例如 *Debug* 或 *Release*) 和平臺設定。 設定的平臺名稱會識別設定的目標環境，例如 API 集或作業系統平臺。 的使用者 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 無法建立平臺; 他們必須從 [專案 VSPackage] 允許的選項中選擇。 當使用者安裝 VSPackage 時，在封裝開發期間建立的傳遞平臺可以根據封裝建立者所設定的任何準則，呈現所需的任何平臺名稱。 然後，使用者就可以在屬性頁具現化時，從 VSPackage 提供的平臺清單中進行選取。

 平臺名稱是選擇性的，因為並非所有專案都支援平臺的概念。 當設定缺少平臺名稱時，在 UI 中會顯示字串 **N/a** 。

 每個解決方案都有自己的一組設定，一次只能有一個作用中。 方案設定是每個專案中的一組不只一項設定。 [不超過] 規定是因為從方案設定中排除專案的選項。 使用者可以建立自己的自訂解決方案設定。

 下表說明專案的一般設定設定。 這些資料列會標示設定名稱和具有平臺名稱的資料行。

|組態名稱|Platform： Win32|平臺： Win64|
|------------------------|----------------------|----------------------|
|*偵錯*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*發行*|\<Release Win32 settings>|\<Release Win64 settings>|
|*Myconfig.xml*|N/A|\<MyConfig Win64 settings>|

> [!NOTE]
> 除非您的目標專案不支援 Win32，否則您無法建立排除 Win32 平臺的 *myconfig.xml* 方案設定。

 變更解決方案的作用中設定，會選取該方案中所建立、執行、調試或部署的專案設定集。 例如，如果您將使用中的方案設定從 [ *發行* ] 變更為 [ *調試* 程式]，則該方案內的所有專案都會自動以方案的 Debug 設定中指出的專案設定來建立。 專案的設定也會命名為 *Debug* ，除非使用者已在環境的設定管理員中進行手動變更。

 針對每個專案儲存的方案設定屬性包含專案名稱、專案設定名稱、旗標，以指出是否要建立或部署，以及平臺名稱。 如需詳細資訊，請參閱 [方案](../../extensibility/internals/solution-configuration.md)設定。

 使用者可以藉由選取階層中的方案 (方案總管) ，然後開啟屬性頁，來查看及設定解決方案設定參數。 同樣地，您可以在方案總管中選取專案，然後開啟該專案的屬性頁，來查看和設定專案設定參數。

 使用者也可以使用發行設定來建立一個專案，並在必要時使用 debug configuration 設定來建立所有其餘專案。 如需詳細資訊，請參閱 [建立的專案](../../extensibility/internals/project-configuration-for-building.md)設定。

 下圖顯示如何執行支援方案和專案設定的介面：

 設定![介面圖形](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")設定介面

 與上圖相關的一些附注：

- `IDispatch` 在設定物件中標示為選用。 具體而言，在流覽物件上具有設定介面是選擇性的。

- `IVsDebuggableProjectCfg` 在設定物件中標示為選擇性，但需要進行偵錯工具才能支援。

- `IVsProjectCfg2` 在設定物件中標示為選擇性，但需要輸出群組支援。

- 設定提供者物件會標示為選擇性物件，但選項是要在其中執行的選項。 您可以在專案物件或個別的物件上，執行物件。

- `IVsCfgProvider2` 需要進行平臺支援和編輯設定。 `IVsCfgProvider` 如果您未執行該功能，就已足夠。

- 在圖表中顯示為個別物件的某些物件，可根據您的特定設計需求，結合到相同的類別中。 不過，在本節的其他主題中，會根據圖表中呈現的案例來討論與這些物件相關聯的物件和介面。

- 某些物件會分開執行。 例如，專案和方案建立會在個別的執行緒上發生，而用來管理組建的物件則與描述組建設定的物件分開。

  如需有關上圖中設定物件介面和設定提供者物件介面的詳細資訊，請參閱 [專案設定物件](../../extensibility/internals/project-configuration-object.md)。 此外， [用於組建的專案](../../extensibility/internals/project-configuration-for-building.md) 設定會提供有關設定產生器和組建相依性物件介面的詳細資訊，以及 [用於管理部署的專案](../../extensibility/internals/project-configuration-for-managing-deployment.md) 設定，會進一步說明附加至設定部署器和部署相依性物件的介面。 最後， [輸出的專案](../../extensibility/internals/project-configuration-for-output.md) 設定會描述輸出群組和輸出物件介面，以及使用屬性頁來查看和設定與設定相關的屬性。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [組建的專案設定](../../extensibility/internals/project-configuration-for-building.md)
- [解決方案設定](../../extensibility/internals/solution-configuration.md)
