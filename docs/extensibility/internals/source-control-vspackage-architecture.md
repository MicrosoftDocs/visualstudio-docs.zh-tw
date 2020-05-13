---
title: 原始碼管理 VS 套件架構 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705076"
---
# <a name="source-control-vspackage-architecture"></a>原始檔控制 VSPackage 架構
原始程式碼管理套件是使用 IDE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的服務的 VS 套件。 作為回報,原始程式碼管理包提供其功能作為原始程式碼管理服務。 此外,原始碼管理套件是一種比原始碼管理外掛程式更通用的替代方法,用於將原始程式碼管理整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]到中 。

 實現原始程式碼管理外掛程式 API 的原始程式管理外掛程式遵守嚴格的協定。 例如,外掛程式不能替換[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]預設 使用者介面 (UI)。 此外,原始程式碼管理外掛程式 API 不能啟用外掛程式來實現其自己的原始程式碼管理模型。 但是,原始程式碼管理包克服了這兩個限制。 原始程式碼管理包可以完全[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]控制 使用者的原始程式碼管理體驗。 此外,原始程式碼管理包可以使用自己的原始程式碼管理模型和邏輯,並且它可以定義所有與原始程式碼管理相關的使用者介面。

## <a name="source-control-package-components"></a>原始碼管理套件元件
 如體系結構圖所示,名為原始程式碼[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理存根的元件是一個 VSPackage,它將原始程式碼管理包[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]與 整合在一起。

 原始程式碼管理存根處理以下任務。

- 提供原始程式碼管理包註冊所需的通用 UI。

- 載入原始碼管理包。

- 將原始程式碼管理包設為活動/非活動。

  源代碼管理存根查找原始程式碼管理包的活動服務,並將所有傳入服務呼叫從IDE路由到該包。

  原始程式碼管理配接器套件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是 提供的特殊原始碼管理包。 此包是基於原始程式碼管理外掛程式 API 支援原始程式碼管理外掛程式的中心元件。 當原始程式碼管理外掛程式是活動外掛程式時,原始程式碼管理取根會將其事件發送到原始程式碼管理配接器包。 反過來,原始程式碼管理配接器包透過使用原始程式碼管理外掛程式 API 與原始碼管理外掛程式通訊,並提供適用於所有原始程式碼管理外掛程式的預設 UI。

  另一方面,當原始程式碼管理包是活動包時,原始程式碼管理存根[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]通過使用原始程式碼管理包介面直接與包通信。 原始程式碼管理包負責託管自己的原始程式碼管理 UI。

  ![Source Control Architecture 圖形](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  對於原始碼管理包,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不提供原始碼或 API 進行整合。 與[創建原始程式碼管理外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)中概述的方法形成對比,其中原始程式碼管理外掛程式必須實現一組嚴格的函數和回調。

  與任何 VSPackage 一樣,原始程式碼管理套件`CoCreateInstance`是可以使用 創建的 COM 物件。 VS包通過實現[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>來使自己對IDE可用。 創建實例後,VSPackage 將接收網站指標和介面<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>,該介面提供對IDE中可用服務和介面的 VSPackage 存取許可權。

  編寫基於 VSPackage 的原始碼管理包需要比編寫基於原始碼管理外掛程式 API 的外掛程式更進階的程式設計專業知識。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [快速入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
