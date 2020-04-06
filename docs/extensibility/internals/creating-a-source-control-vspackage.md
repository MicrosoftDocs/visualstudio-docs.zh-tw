---
title: 建立原始碼管理 VS 套件 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709183"
---
# <a name="create-a-source-control-vspackage"></a>建立原始碼管理 VS 套件
本文檔包括指向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]與 整合的原始程式碼管理套件的體系結構概述的連結、由要實現的介面定義的 API 和要使用的服務,以及說明簡單原始程式碼管理包實現的範例。

 使用原始碼管理 VSPackage,您可以建立深度整合路徑,以便原始程式碼[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理與整合。 它使包能夠繞過由承載的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]預設原始程式碼管理 UI,回應來自專案系統的原始程式碼管理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]請求,並與**解決方案資源管理員**等元件進行交互。 授權[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)][!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]合作夥伴創建 VSPackage 的機制,該功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可與 使用服務模型集成。

## <a name="in-this-section"></a>本節內容
- [開始使用](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 討論原始碼管理套件,它是原始程式碼管理外掛程式的更進階替代方法,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用於在中實現原始程式碼管理功能。

- [架構](../../extensibility/internals/source-control-vspackage-architecture.md)

 提供關係圖並解釋原始程式碼管理包的元件。

- [特性](../../extensibility/internals/source-control-vspackage-features.md)

 描述原始碼管理套件的各種功能。

- [設計項目](../../extensibility/internals/source-control-vspackage-design-elements.md)

 描述原始碼管理套件必須實現的 VS 套件的結構,以便進行深度整合。

## <a name="related-sections"></a>相關章節
- [建立原始碼管理外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)

 討論如何創建原始程式碼管理外掛程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],在原始程式碼管理使用者介面(UI) 中提供原始程式碼管理功能。

- [原始碼管理](../../extensibility/internals/source-control.md)

 討論了實現原始碼管理作為的整合功能的選項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。
