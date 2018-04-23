---
title: 來源控制 VSPackage 架構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a423b270eb8a26e9573f957da48915db37bf6851
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-vspackage-architecture"></a>原始檔控制 VSPackage 架構
原始檔控制封裝是使用 VSPackage 服務[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 所提供。 傳回，原始檔控制封裝提供原始檔控制服務的功能。 此外，原始檔控制封裝是功能更多樣的替代方式的原始檔控制整合到原始檔控制外掛程式比[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制外掛程式，用來實作原始檔控制外掛程式 API 遵守嚴格的合約。 例如，外掛程式無法取代預設[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者介面 (UI)。 此外，原始檔控制外掛程式 API 不會啟用的外掛程式來實作其本身的原始檔控制模型。 原始檔控制封裝時，不過，克服這兩個這些限制。 原始檔控制封裝具有完整控制權的原始檔控制經驗[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者。 此外，原始檔控制封裝可使用它自己的原始檔控制模型和邏輯，而且它可以定義所有原始檔控制相關的使用者介面。  
  
## <a name="source-control-package-components"></a>原始檔控制封裝元件  
 架構在圖表中所示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]元件命名為原始檔控制虛設常式是整合的原始檔控制封裝的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制虛設常式會處理下列工作。  
  
-   提供所需的原始檔控制套件登錄的通用 UI。  
  
-   載入原始檔控制封裝。  
  
-   設定原始檔控制封裝做為作用中/非作用中。  
  
 原始檔控制虛設常式會尋找原始檔控制封裝的作用中服務，並將路由從 IDE 所有內送的服務呼叫，該封裝。  
  
 原始檔控制配接器套件是特殊的原始檔控制封裝的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供。 此套件是用於支援原始檔控制外掛程式原始檔控制外掛程式 API 為基礎的主要元件。 外掛程式的作用中的原始檔控制外掛程式時，原始檔控制虛設常式其將事件傳送到原始檔控制配接器套件。 接著，原始檔控制配接器套件會使用原始檔控制外掛程式 API 與原始檔控制外掛程式通訊，同時還提供預設值是很常見的所有原始檔控制外掛程式的 UI。  
  
 使用中的封裝的原始檔控制封裝時，相反地，原始檔控制 Stub 直接與封裝會使用通訊[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]原始檔控制封裝的介面。 原始檔控制封裝負責裝載它自己的原始檔控制 UI。  
  
 ![Source Control Architecture 圖形](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 原始檔控制封裝，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不提供原始程式碼控制或 API 進行整合。 以此中所述的方法和[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)原始檔控制外掛程式對實作固定的一組函式和回呼。  
  
 原始檔控制封裝就像是任何 VSPackage，可以使用建立 COM 物件`CoCreateInstance`。 VSPackage 會使本身可[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由實作 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 時建立執行個體之後，接收網站指標和<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>提供 VSPackage 存取可用的服務和介面，在 IDE 中的介面。  
  
 撰寫 VSPackage 為基礎的原始檔控制封裝需要更進階的程式設計專業知識，比撰寫原始檔控制外掛程式 API 為基礎外掛程式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [快速入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)