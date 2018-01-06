---
title: "IDebugProperty2::GetDerivedMostProperty |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords: IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4e9efd498485340b49dbd385a6a94fa6cf7fcedd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
取得屬性的最具衍生性屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppDerivedMost`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，代表最具衍生性屬性。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則會傳回錯誤碼。 傳回`S_GETDERIVEDMOST_NO_DERIVED_MOST`如果擷取沒有最具衍生性屬性。  
  
## <a name="remarks"></a>備註  
 例如，如果這個屬性描述的物件，實作`ClassRoot`但這是實際的具現化`ClassDerived`衍生自`ClassRoot`，則這個方法會傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件描述`ClassDerived`物件。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)