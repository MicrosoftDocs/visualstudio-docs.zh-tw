---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e64df5e58f396462ebc9309302a7bbb7a42febcf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006290"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
這個方法會擷取從程式的別名清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `uRequest`  
 [in]別名，以傳回的最大數目 (指定長度的陣列傳遞至`ppAliases`)。  
  
 `ppAliases`  
 [in、 out]別名所填入的陣列 (如果這個值是 null 值和`uRequest`為 0，就會傳回別名可傳回的計數`puFetched`)。  
  
 `puFetched`  
 [out]傳回取得的別名的數字。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)