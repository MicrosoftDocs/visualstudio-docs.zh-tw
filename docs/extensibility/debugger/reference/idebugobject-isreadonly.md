---
title: "IDebugObject::IsReadOnly |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::IsReadOnly
helpviewer_keywords: IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 973e3b2b85012157d90fb09e9be669f83b7c9147
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
判斷此物件是否為唯讀。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfIsReadOnly`  
 [out]傳回非零 (`TRUE`) 如果此物件是唯讀的; 否則傳回零 (`FALSE`)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 唯讀的物件不能有它建立之後變更其值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)