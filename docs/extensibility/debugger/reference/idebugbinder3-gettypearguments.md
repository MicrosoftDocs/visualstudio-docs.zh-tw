---
title: "IDebugBinder3::GetTypeArguments |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetTypeArguments
helpviewer_keywords: IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7aff11599f00ad417915c4cb4f4e6ad907b5660d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
這個方法會擷取與此物件相關聯的引數類型的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `skip`  
 [in]略過快速入門的引數類型的欄位數目。  
  
 `count`  
 [in]引數要傳回的欄位數目 (也會指定的大小`ppFields`陣列)。  
  
 `ppFields`  
 [in、 out]將會填入這個方法傳回的欄位的陣列。  
  
 `pFetched`  
 [out]\(選擇性)實際傳回的欄位類型的引數數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 引數類型的數字可以事先取得與[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)