---
title: 原始檔控制 VSPackage 架構 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9484aabd0080b0a44d75a8a5f6d90d9217d74b8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723357"
---
# <a name="source-control-vspackage-architecture"></a>原始檔控制 VSPackage 架構
原始檔控制封裝是使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 提供之服務的 VSPackage。 在傳回時，原始檔控制封裝會提供其功能作為原始檔控制服務。 此外，原始檔控制套件比原始檔控制外掛程式更具彈性，可將原始檔控制整合到 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

 原始檔控制外掛程式，可執行嚴格合約所遵守美國的原始檔控制外掛程式 API。 例如，外掛程式無法取代預設的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用者介面（UI）。 此外，原始檔控制外掛程式 API 不會啟用外掛程式來執行它自己的原始檔控制模型。 不過，原始檔控制封裝也克服了這兩項限制。 原始檔控制封裝可完整控制 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用者的原始檔控制體驗。 此外，原始檔控制封裝也可以使用自己的原始檔控制模型和邏輯，而且可以定義所有與原始檔控制相關的使用者介面。

## <a name="source-control-package-components"></a>原始檔控制封裝元件
 如架構圖所示，名為原始檔控制存根的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 元件，是將原始檔控制封裝與 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合的 VSPackage。

 原始檔控制存根會處理下列工作。

- 提供原始檔控制封裝註冊所需的通用 UI。

- 載入原始檔控制封裝。

- 將原始檔控制封裝設定為作用中/非作用中。

  原始檔控制存根會尋找原始檔控制封裝的使用中服務，並將所有來自 IDE 的傳入服務呼叫路由傳送至該封裝。

  原始檔控制介面卡套件是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供的特殊原始檔控制套件。 此套件是以原始檔控制外掛程式 API 為基礎支援原始檔控制外掛程式的中央元件。 當原始檔控制外掛程式是使用中的外掛程式時，原始檔控制存根會將其事件傳送至原始檔控制介面卡封裝。 接著，原始檔控制介面卡封裝會使用原始檔控制外掛程式 API 與原始檔控制外掛程式通訊，同時也提供所有原始檔控制外掛程式通用的預設 UI。

  另一方面，當原始檔控制封裝是作用中的封裝時，原始檔控制存根會使用 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 的原始檔控制封裝介面，直接與封裝進行通訊。 原始檔控制套件會負責裝載自己的原始檔控制 UI。

  ![原始檔控制架構圖形](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  針對原始檔控制封裝，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 不會提供原始檔控制程式代碼或用於整合的 API。 相較之下，[建立原始](../../extensibility/internals/creating-a-source-control-plug-in.md)檔控制外掛程式必須執行一組固定的函式和回呼，這是一種方法。

  就像任何 VSPackage，原始檔控制封裝是可以使用 `CoCreateInstance` 建立的 COM 物件。 VSPackage 會藉由執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>，讓它自己可供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 使用。 建立實例之後，VSPackage 會接收網站指標和 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 介面，以提供 IDE 中可用服務和介面的 VSPackage 存取權。

  撰寫以 VSPackage 為基礎的原始檔控制套件，需要比撰寫原始檔控制外掛程式 API 的外掛程式更先進的程式設計專長。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [使用者入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)