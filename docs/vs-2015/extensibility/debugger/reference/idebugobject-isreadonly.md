---
title: IDebugObject::IsReadOnly |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 310b5609b999cd21fae73f31085c258c762e2917
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490869"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugObject::IsReadOnly](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-isreadonly)。  
  
判斷這個物件是否為唯讀。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [out]會傳回非零 (`TRUE`) 如果此物件是唯讀的; 否則會傳回零 (`FALSE`)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 唯讀的物件不能有它建立之後變更其值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

