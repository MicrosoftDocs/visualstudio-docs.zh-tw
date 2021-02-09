---
title: 建立原始檔控制外掛程式 |Microsoft Docs
description: 瞭解如何建立原始檔控制外掛程式，以將原始檔控制功能新增至 (IDE) 的 Visual Studio 整合式開發環境。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 489aea2ba5b12dafa161ce70a49f81f60b38ba5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878756"
---
# <a name="create-a-source-control-plug-in"></a>建立原始檔控制外掛程式
Visual Studio SDK 提供的資源可讓您將原始檔控制功能新增至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) 的整合式開發環境。 它可讓您使用符合本檔中所述之原始檔控制外掛程式 API 的任何外掛程式 DLL。

## <a name="in-this-section"></a>本節內容
- [開始使用](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 描述如何安裝原始檔控制外掛程式，並強調目前可用的原始檔控制外掛程式 API 版本。

- [架構](../../extensibility/internals/source-control-plug-in-architecture.md)

 使用架構圖來說明如何將原始檔控制外掛程式與 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 整合。

- [測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 提供如何測試原始檔控制外掛程式之安裝和操作的指引。

## <a name="related-sections"></a>相關章節
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 討論如何建立原始檔控制 VSPackage，而不只提供原始檔控制功能，而是取代 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 原始檔控制 UI。

- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)

 提供原始檔控制外掛程式 API 中所有元素的完整清單。

- [原始檔控制](../../extensibility/internals/source-control.md)

 討論將原始檔控制實作為的整合式功能的選項 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。
