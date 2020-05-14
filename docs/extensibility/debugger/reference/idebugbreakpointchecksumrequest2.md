---
title: IDebug 突破點檢查和請求2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 632c3611f6c03a47a7d46e985eb6aa2685864a7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735122"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
表示斷點請求的文檔校驗和。

## <a name="syntax"></a>語法

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]調試包實現,由調試引擎使用。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugBreakpointChecksumRequest2`。

|方法|描述|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|檢索斷點請求的文檔校驗和,給定要使用的校驗和演演演算法的唯一標識符。|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|確定是否為此文檔啟用了校驗和。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
