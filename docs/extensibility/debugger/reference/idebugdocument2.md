---
title: IDebugDocument2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c959c018dd4da0ff088c4fb52c0420de83b4eac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731985"
---
# <a name="idebugdocument2"></a>IDebugDocument2
此介面表示源文檔。

## <a name="syntax"></a>語法

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]通常實現此介面。 除錯引擎 (DE) 也可以實現此介面,當它需要提供原始碼,並且磁碟上不存在原始程式碼時。  在這種情況下,DE 還將實現[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)和[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)介面,以及[IDebugdisassemblystream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)和[IDebugDocumentE2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)介面上的一些其他方法。

## <a name="notes-for-callers"></a>通話備註
 上`IDebugDocumentContext2`的方法`IDebugDisassemblyStream2`,`IDebugDocumentPosition2``IDebugActivateDocumentEvent2`和介面返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugDocument2`。

|方法|描述|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|以幾種形式之一獲取文檔的名稱。|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|獲取文檔的類標識碼。|

## <a name="remarks"></a>備註
 僅當 DE 提供原始程式碼時,才實現此介面。 例如,當您在 HTML 頁上調試腳本時,DE 提供原始碼,因為原始碼是動態下載或生成的,並且不存在為磁碟檔。 調試傳統語言(如C++)時,不需要實現此介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
