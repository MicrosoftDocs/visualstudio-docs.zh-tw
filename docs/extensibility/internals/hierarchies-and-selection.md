---
title: 階層和選取專案 |Microsoft Docs
description: 瞭解 Visual Studio 如何處理專案等階層，以及它如何使用選取內容來判斷要向使用者顯示的內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04f433e3da45e10d2b1721ac13254856489d2d0a
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480417"
---
# <a name="hierarchies-and-selection"></a>階層和選取範圍
當您自訂時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您應該瞭解如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 處理專案等階層，以及它如何使用選取內容來判斷要向使用者顯示的內容。 本節討論階層 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 和選取的概念。

## <a name="in-this-section"></a>本節內容
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)

 描述專案階層和階層的一般概念。

- [IDE 中的選取專案和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 描述 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 如何維護使用者目前作用中物件的相關資訊，並讓 vspackage track 的貨幣。

- [選取專案內容物件](../../extensibility/internals/selection-context-objects.md)

 討論如何在視窗上判斷使用者的選取內容焦點的模型。

- [對使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)

 討論中的可用功能如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根據使用者目前的選取範圍內容和整體的 IDE 內容。

## <a name="related-sections"></a>相關章節
- [專案類型架構](../../extensibility/internals/project-types-architecture.md)

 提供有關專案類型的詳細技術資訊。
