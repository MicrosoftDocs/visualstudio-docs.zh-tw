---
title: IEEDataStorage::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 11
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 60176876d9eba4b599348c562b812deec9fae589
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Returns the number of bytes contained in this object.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```cs  
int GetSize(  
   out uint size  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `size`  
 [out] The number of bytes contained in this object.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Use the [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) method to retrieve the actual data bytes.  
  
## <a name="see-also"></a>See Also  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
