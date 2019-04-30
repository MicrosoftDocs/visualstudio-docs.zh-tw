---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 584c7ba10ac9eb05268f50ecaffa8c47818f7977
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915541"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
擷取一份此執行緒的堆疊框架。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

#### <a name="parameters"></a>參數
 `dwFieldSpec`

 [in]從旗標的組合[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)列舉，指定哪些欄位[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構是填寫。指定`FIF_FUNCNAME_FORMAT`格式化成單一字串的函式名稱的旗標。

 `nRadix`

 [in]格式化數值列舉值中的資訊使用的基數。

 `ppEnum`

 [out]傳回[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)物件，其中包含一份[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構描述的堆疊框架。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 執行緒的框架列舉順序，與目前的框架先列舉和列舉上次最舊的畫面格。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)