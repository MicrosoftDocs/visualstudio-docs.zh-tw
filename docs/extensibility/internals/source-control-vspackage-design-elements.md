---
title: 原始檔控制 VSPackage 的設計元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e9b22ea32698d6e996bfee618b0b5ca4da5943d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322473"
---
# <a name="source-control-vspackage-design-elements"></a>原始檔控制 VSPackage 的設計項目
在本節中的主題說明結構原始檔控制 VSPackage 必須實作的深度整合。 也會列出介面的原始檔控制 VSPackage 的服務可以實作，並從其他介面和服務可以使用原始檔控制 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]元件來支援它的來源控制模型與功能。

## <a name="in-this-section"></a>本節內容
- [VSPackage 結構](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 定義原始檔控制 VSPackage 結構。

- [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 列出原始檔控制套件的相關介面和服務。

- [提供的服務](../../extensibility/internals/services-provided-source-control-vspackage.md)

 描述原始檔控制 VSPackage 所提供的原始檔控制服務。

## <a name="related-sections"></a>相關章節
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 討論如何建立原始檔控制 VSPackage，不僅提供原始檔控制功能，但可以用來自訂[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制 UI。