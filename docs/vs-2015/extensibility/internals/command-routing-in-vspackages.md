---
title: Vspackage 中的命令路由 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 954d3f25a425652d8adcb31bd36fab06de0d04d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195081"
---
# <a name="command-routing-in-vspackages"></a>在 VSPackage 中路由傳送命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

命令會 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 根據其執行所在的內容路由傳送。 它會從初始內容向外路由傳送至全域內容。  
  
## <a name="in-this-section"></a>本節內容  
 [路由演算法](../../extensibility/internals/command-routing-algorithm.md)  
 描述命令路由解析的順序。  
  
 [可用性](../../extensibility/internals/command-availability.md)  
 討論命令路由。  
  
 [使用 Interop 組件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 討論 managed 程式碼與 COM 之間路由命令的考慮。  
  
## <a name="related-sections"></a>相關章節  
 [選取項目內容物件](../../extensibility/internals/selection-context-objects.md)  
 討論如何在視窗上判斷使用者的選取內容焦點的模型。  
  
 [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)  
 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。
