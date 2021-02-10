---
title: Interop 元件中的命令合約 |Microsoft Docs
description: 深入瞭解透過 VisualStudio 介面處理命令的基本合約（IOleCommandTarget 介面）。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ed9435f4f0618ee0c0f4bc47cdb21e2cbf92f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940120"
---
# <a name="command-contracts-in-interop-assemblies"></a>Interop 元件中的命令合約
透過介面處理命令的基本合約 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 是，環境會呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法來判斷是否支援命令，並在支援時判斷其狀態和文字。 然後，環境會呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法來執行命令。

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>所有命令的方法處理方式都相同。 此外，如有必要 (（例如，) 的下拉式清單） <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 使用適當的參數呼叫方法來管理。 這些參數的解讀取決於指定的命令。

 如果命令目標在 output 參數中傳回值，則呼叫端一律負責釋放任何已配置的資源。 因為這個參數是變異，所以清除變異會釋出資源。

 如果命令必須在階層視窗內運作，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 必須使用介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面具有類似的合約，其方法如下： <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 。

## <a name="see-also"></a>另請參閱
- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)
- [命令執行](../../extensibility/internals/command-implementation.md)
