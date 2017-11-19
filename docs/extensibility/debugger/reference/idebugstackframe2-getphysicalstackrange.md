---
title: "IDebugStackFrame2::GetPhysicalStackRange |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords: IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2b57cc7b5959f82b5f02c4939d6645c30c1c706
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
取得電腦相關的堆疊框架相關聯的實體位址範圍的表示。  
  
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
 [out]傳回最高的實體位址，此堆疊框架相關聯。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的資訊可由工作階段的偵錯管理員 (SDM) 來排序的堆疊框架。  
  
 它會假設，呼叫堆疊高到低排列，也就是，新的堆疊框架會加入在逐漸較低的記憶體位址。 執行階段架構必須提供符合這個假設的實體堆疊範圍。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)