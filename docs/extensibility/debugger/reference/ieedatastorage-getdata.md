---
title: IEEDataStorage::GetData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 7
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
ms.openlocfilehash: f9642911606d9bbd72382fa1209484cded9bdf74
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Retrieves the specified number of bytes from the object.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `dataSize`  
 [in] The number of bytes to retrieve (the `data` array must hold at least this number of bytes).  
  
 `sizeGotten`  
 [out] Returns the number of bytes actually retrieved.  
  
 `data`  
 [in, out] Array to be filled in with the requested data.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The recommended use of this method is to retrieve all the data bytes into a local array, since there is no way to skip over bytes in the retrieval process. In this case, the parameter `dataSize` should be the value returned by the [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) method.  
  
## <a name="see-also"></a>See Also  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
