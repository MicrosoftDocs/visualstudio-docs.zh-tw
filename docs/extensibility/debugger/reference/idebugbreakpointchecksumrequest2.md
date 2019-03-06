---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfad0d8469a3cd01b5697cd9ba74f7a84ee84b83
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706271"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
表示中斷點要求的文件總和檢查碼。

## <a name="syntax"></a>語法

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 藉由實作[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯封裝，而且由偵錯引擎。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugBreakpointChecksumRequest2`。

|方法|描述|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|擷取的中斷點要求指定總和檢查碼演算法的唯一識別項使用的文件總和檢查碼。|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|判斷是否已啟用這份文件的總和檢查碼。|

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll