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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196962"
---
# <a name="creating-a-source-control-vspackage"></a>建立原始檔控制 VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本檔包含與整合之原始檔控制套件的架構總覽連結、所 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 要執行之介面所定義的 API，以及要使用的服務，以及示範簡單原始檔控制封裝執行的範例。  
  
 使用原始檔控制 VSPackage，您可以建立與整合的原始檔控制的深層整合路徑 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 它可讓封裝略過所裝載的預設原始檔控制 UI [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，回應專案系統的原始檔控制要求，並與 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **方案總管**等元件互動。 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 可讓夥伴使用一種機制來建立可與 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 使用服務模型整合的 VSPackage。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 討論原始檔控制封裝，這是在中執行原始檔控制功能的原始檔控制外掛程式更先進的替代方案 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [架構](../../extensibility/internals/source-control-vspackage-architecture.md)  
 提供圖表，並說明原始檔控制封裝的元件。  
  
 [功能](../../extensibility/internals/source-control-vspackage-features.md)  
 描述原始檔控制封裝的各種功能。  
  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 描述原始檔控制封裝必須針對深層整合執行的 VSPackage 結構。  
  
## <a name="related-sections"></a>相關章節  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 討論如何建立原始檔控制外掛程式，以提供原始檔控制使用者介面中的原始檔控制功能 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (UI) 。  
  
 [原始檔控制](../../extensibility/internals/source-control.md)  
 討論將原始檔控制實作為的整合式功能的選項 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。
