---
title: 建立原始檔控制 VSPackage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930291"
---
# <a name="creating-a-source-control-vspackage"></a>建立原始檔控制 VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

這份文件包含連結架構的概觀與整合的原始檔控制封裝[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，定義要實作的介面，並使用，服務的 API，並說明簡單的原始程式碼的範例控制封裝的實作。  
  
 您可以使用原始檔控制 VSPackage，建立原始檔控制整合的深度整合路徑[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 它讓套件能夠略過預設原始檔控制所裝載的 UI [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、 來源控制要求回應來自專案系統，並與其互動[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]元件這類**方案總管 中**。 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]可讓[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]合作夥伴建立 VSPackage 可以將整合的一套機制[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]使用服務模型。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 討論原始檔控制套件，這是更進階的替代方式，以原始檔控制外掛程式的實作中的原始檔控制功能[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
 [架構](../../extensibility/internals/source-control-vspackage-architecture.md)  
 顯示圖表，並說明原始檔控制套件的元件。  
  
 [功能](../../extensibility/internals/source-control-vspackage-features.md)  
 描述原始檔控制套件的各種功能。  
  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 描述原始檔控制套件必須緊密結合為實作 VSPackage 的結構。  
  
## <a name="related-sections"></a>相關章節  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 討論如何建立原始檔控制外掛程式，提供在原始檔控制功能[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]原始檔控制使用者介面 (UI)。  
  
 [原始檔控制](../../extensibility/internals/source-control.md)  
 討論用來實作原始檔控制的整合功能，為選項[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。
