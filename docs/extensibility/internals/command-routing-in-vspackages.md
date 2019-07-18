---
title: 命令在 Vspackage 中路由傳送 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a534a015f57a738ca65895002a6fec4454f0ae97
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342231"
---
# <a name="command-routing-in-vspackages"></a>在 Vspackage 中路由傳送命令
命令路由傳入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根據它的執行的內容。 它是通用的內容路由傳送從向外的初步內容。

## <a name="in-this-section"></a>本節內容
- [命令路由演算法](../../extensibility/internals/command-routing-algorithm.md)

 描述命令路由對解析順序。

- [命令可用性](../../extensibility/internals/command-availability.md)

 討論命令路由。

- [使用 interop 組件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 討論 managed 程式碼與 COM 之間的路由命令的注意事項

## <a name="related-sections"></a>相關章節
- [選取內容物件](../../extensibility/internals/selection-context-objects.md)

 討論如何判斷使用者的選取項目內容焦點視窗上的模型。

- [命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。