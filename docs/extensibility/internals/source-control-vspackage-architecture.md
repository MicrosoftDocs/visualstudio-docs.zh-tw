---
title: 原始檔控制 VSPackage 架構 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a9fb208c011b4594cde7a00a586f5d7c98ae7a6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937947"
---
# <a name="source-control-vspackage-architecture"></a>原始檔控制 VSPackage 架構
原始檔控制封裝是使用 VSPackage 的服務會[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 所提供。 原始檔控制套件提供原始檔控制服務的功能。 此外，原始檔控制封裝是一個更靈活的替代方式，比原始檔控制整合到原始檔控制外掛程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制外掛程式實作原始檔控制外掛程式 API 會遵守嚴格的合約。 比方說，外掛程式無法取代預設[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者介面 (UI)。 此外，原始檔控制外掛程式 API 不會啟用外掛程式，以實作自己的原始檔控制模型。 不過，原始檔控制封裝，克服了這兩個這些限制。 原始檔控制封裝具有完整控制權的原始檔控制體驗[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者。 此外，原始檔控制封裝可使用它自己的原始檔控制模型和邏輯，而且它可以定義所有原始檔控制相關的使用者介面。  
  
## <a name="source-control-package-components"></a>原始檔控制封裝元件  
 架構圖表所示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]名為原始檔控制虛設常式的元件是整合的原始檔控制封裝的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制虛設常式會處理下列工作。  
  
- 提供所需的原始檔控制套件登錄的共同 UI。  
  
- 載入原始檔控制封裝。  
  
- 將原始檔控制封裝設定為 作用中/非作用中。  
  
  原始檔控制虛設常式會尋找原始檔控制封裝的作用中的服務，並將路由從 IDE 所有內送的服務呼叫，該封裝。  
  
  原始檔控制配接器套件是特殊的原始檔控制套件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供。 此封裝是用於支援原始檔控制外掛程式原始檔控制外掛程式 API 為基礎的主要元件。 外掛程式使用原始檔控制外掛程式時，原始檔控制虛設常式其將事件傳送至原始檔控制配接器套件。 接著，原始檔控制配接器套件會使用原始檔控制外掛程式 API 通訊協定與原始檔控制外掛程式，同時也提供 預設值是很常見的所有原始檔控制外掛程式的 UI。  
  
  原始檔控制套件的使用中的封裝時，相反地，原始檔控制虛設常式，直接進行通訊與封裝使用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]原始檔控制封裝的介面。 原始檔控制封裝負責裝載自己的原始檔控制 UI。  
  
  ![Source Control Architecture 圖形](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  原始檔控制封裝，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不提供原始程式碼控制或 API 整合。 這與中所述的方法相反[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)原始檔控制外掛程式必須實作固定的一份函式和回呼的位置。  
  
  任何的 VSPackage，例如原始檔控制封裝是一個 COM 物件，可以建立使用`CoCreateInstance`。 VSPackage 會使本身能夠[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由實作 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 建立執行個體後，收到的站台的指標和<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>提供 VSPackage 存取可用的服務和介面，在 IDE 中的介面。  
  
  撰寫 VSPackage 為基礎的原始檔控制套件需要更進階的程式設計專業知識，比起撰寫以原始檔控制外掛程式 API 為基礎的外掛程式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [快速入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)