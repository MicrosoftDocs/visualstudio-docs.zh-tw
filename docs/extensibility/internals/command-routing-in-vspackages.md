---
title: Vspackage 中的命令路由 |Microsoft Docs
description: 瞭解 Vspackage 中的命令路由，以及如何根據在 Visual Studio 中執行命令的內容來路由傳送命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8168fbe3ad5ba9b1b332aebc4675ecd8e752ee7e
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305227"
---
# <a name="command-routing-in-vspackages"></a>Vspackage 中的命令路由
命令會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根據其執行所在的內容路由傳送。 它會從初始內容向外路由傳送至全域內容。

## <a name="in-this-section"></a>本節內容
- [命令路由演算法](../../extensibility/internals/command-routing-algorithm.md)

 描述命令路由解析的順序。

- [命令可用性](../../extensibility/internals/command-availability.md)

 討論命令路由。

- [使用 interop 元件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 討論 managed 程式碼與 COM 之間路由命令的考慮。

## <a name="related-sections"></a>相關章節
- [選取專案內容物件](../../extensibility/internals/selection-context-objects.md)

 討論如何在視窗上判斷使用者的選取內容焦點的模型。

- [命令、功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。
