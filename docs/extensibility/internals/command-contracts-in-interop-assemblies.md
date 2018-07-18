---
title: 命令 Interop 組件中的合約 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfb60bb4fdc0a633ecee92c47b8465f794416bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127369"
---
# <a name="command-contracts-in-interop-assemblies"></a>Interop 組件中的命令合約
處理命令的基本合約<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面是環境呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法來決定是否支援該命令，如果支援，以判斷其狀態和文字。 接著，環境會呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法才能執行命令。  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法相同的方式處理所有命令。 其他的通訊 （例如，使用下拉式清單），必要時受呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>使用適當參數的方法。 這些參數的解譯取決於指定的命令。  
  
 如果在命令目標的輸出參數中傳回值，呼叫端負責一律釋放已配置的任何資源。 這個參數是變數，因為清除 variant 釋放資源。  
  
 在其中命令必須在階層架構視窗運作的情況下<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>必須使用介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面具有類似的合約與類似的方法：<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)   
 [實作](../../extensibility/internals/command-implementation.md)