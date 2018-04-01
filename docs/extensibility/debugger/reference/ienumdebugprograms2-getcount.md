---
title: IEnumDebugPrograms2::GetCount |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2::GetCount
helpviewer_keywords:
- IEnumDebugPrograms2::GetCount
ms.assetid: 84832982-fa68-4090-a5b7-b233817876b7
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c74e14ee32d58a638cc4c60f98aca1ca26e4c075
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugprograms2getcount"></a>IEnumDebugPrograms2::GetCount
列舉中傳回的項目數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcelt`  
 [out]列舉中傳回的項目數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法不是指定的自訂 COM 列舉介面的一部分`Next`， `Clone`， `Skip`，和`Reset`必須實作的方法。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)