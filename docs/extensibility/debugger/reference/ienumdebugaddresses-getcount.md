---
title: "IEnumDebugAddresses::GetCount |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 248cdee07ea9a607e1df4a04e003ed5db2d1f3f1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
這個方法會傳回在列舉中的項目數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
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
 這個方法不是慣用的 COM 列舉介面會指定只有下一步、 複製、 Skip 和重設需要實作的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
