---
title: "IDebugBinder3::GetAllAliases |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetAllAliases
helpviewer_keywords: IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57f644cb0f5cb550e093ccc2691fed91e9f5f4b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
這個方法會擷取程式的別名清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `uRequest`  
 [in]別名，以傳回的最大數目 (指定傳遞至陣列的長度`ppAliases`)。  
  
 `ppAliases`  
 [in、 out]別名所填入的陣列 (如果這是 null 值和`uRequest`是 0，則會傳回別名可傳回的計數`puFetched`)。  
  
 `puFetched`  
 [out]傳回取得的別名的數量。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)