---
title: 建立原始檔控制 VSPackage |Microsoft Docs
description: 瞭解如何建立原始檔控制 VSPackage，以建立原始檔控制的深層整合路徑以與 Visual Studio 整合。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9be8b97b3e37a224b12781e66543f7ab126f2c6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958527"
---
# <a name="create-a-source-control-vspackage"></a>建立原始檔控制 VSPackage
本檔包含與整合之原始檔控制套件的架構總覽連結、所 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 要執行之介面所定義的 API，以及要使用的服務，以及示範簡單原始檔控制封裝執行的範例。

 使用原始檔控制 VSPackage，您可以建立與整合的原始檔控制的深層整合路徑 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 它可讓封裝略過所裝載的預設原始檔控制 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，回應專案系統的原始檔控制要求，並與 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **方案總管** 等元件互動。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可讓夥伴使用一種機制來建立可與 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用服務模型整合的 VSPackage。

## <a name="in-this-section"></a>本節內容
- [開始使用](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 討論原始檔控制封裝，這是在中執行原始檔控制功能的原始檔控制外掛程式更先進的替代方案 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [架構](../../extensibility/internals/source-control-vspackage-architecture.md)

 提供圖表，並說明原始檔控制封裝的元件。

- [功能](../../extensibility/internals/source-control-vspackage-features.md)

 描述原始檔控制封裝的各種功能。

- [設計項目](../../extensibility/internals/source-control-vspackage-design-elements.md)

 描述原始檔控制封裝必須針對深層整合執行的 VSPackage 結構。

## <a name="related-sections"></a>相關章節
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)

 討論如何建立原始檔控制外掛程式，以提供原始檔控制使用者介面中的原始檔控制功能 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (UI) 。

- [原始檔控制](../../extensibility/internals/source-control.md)

 討論將原始檔控制實作為的整合式功能的選項 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。
