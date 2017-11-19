---
title: "IDebugPointerObject3::GetPointerAddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetPointerAddress
- IDebugPointerObject3::GetPointerAddress
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aff3dcc29c58038e95bfb80a52e8c38928d802d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpointerobject3getpointeraddress"></a>IDebugPointerObject3::GetPointerAddress
擷取指標的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPointerAddress (  
   UINT64* puAddress  
);  
```  
  
```csharp  
int GetPointerAddress (  
   out ulong puAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `puAddress`  
 [out]傳回指標的位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)