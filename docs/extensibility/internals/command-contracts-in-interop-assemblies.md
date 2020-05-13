---
title: 互通程式集中的命令協定 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709678"
---
# <a name="command-contracts-in-interop-assemblies"></a>互通程式集中的命令協定
通過<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面處理命令的基本協定是,環境調<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>用 方法以確定該命令是否受支援,如果支援該命令,則確定其狀態和文本。 然後,環境調用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法執行命令。

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>該方法對所有命令的處理方式相同。 如果需要,通過使用適當的參數調用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法來管理進一步的通信(例如,使用下拉清單)。 這些參數的解釋取決於指定的命令。

 如果命令目標返回輸出參數中的值,則調用方始終負責釋放已分配的任何資源。 由於此參數是變體,因此清除變體將釋放資源。

 如果命令必須在層次結構視窗中運行,<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>則必須使用介面。 介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>具有類似的協定,其方法相似<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>:<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>和 。

## <a name="see-also"></a>另請參閱
- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VS 套件的指令路由](../../extensibility/internals/command-routing-in-vspackages.md)
- [命令執行](../../extensibility/internals/command-implementation.md)
