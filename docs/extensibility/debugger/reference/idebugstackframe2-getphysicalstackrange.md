---
title: IDebugStackFrame2::GetPhysicalStackRange |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1b46dd9993eb8a7611b4d84211016168d609101
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950377"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
取得的堆疊框架相關聯的實體位址範圍的電腦相關表示法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>參數  
 `paddrMin`  
 [out]傳回此堆疊框架相關聯的最小實體位址。  
  
 `paddrMax`  
 [out]傳回此堆疊框架相關聯的最高的實體位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的資訊供工作階段的偵錯管理員 (SDM) 中，來排序的堆疊框架。  
  
 它會假設，呼叫堆疊成長時，也就是，在越來越多的較低的記憶體位址，會新增新的堆疊框架。 執行階段架構必須提供符合這項假設的實體堆疊範圍。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)