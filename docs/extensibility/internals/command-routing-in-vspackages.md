---
title: VS 包中的命令路由 |微軟文件
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
ms.openlocfilehash: 957ddcca46365a882609c15c96d666c2848ace6c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709547"
---
# <a name="command-routing-in-vspackages"></a>VS 套件的指令路由
命令根據執行命令的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]上下文路由。 它將從初始上下文路由到全域上下文。

## <a name="in-this-section"></a>本節內容
- [命令路由演演算法](../../extensibility/internals/command-routing-algorithm.md)

 描述命令路由解析的順序。

- [命令可用性](../../extensibility/internals/command-availability.md)

 討論命令路由。

- [使用互通程式集的指令和選單](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 討論託管代碼和 COM 之間路由命令中的注意事項。

## <a name="related-sections"></a>相關章節
- [選擇內容物件](../../extensibility/internals/selection-context-objects.md)

 討論如何確定用戶選擇上下文對視窗的關注模型。

- [命令、選單和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。
