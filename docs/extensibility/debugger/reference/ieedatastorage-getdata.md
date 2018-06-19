---
title: IEEDataStorage::GetData |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ddbc77950396df743b88ce3b6c1a94bbeaf8126
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120851"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
從物件擷取指定的位元組數目。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `dataSize`  
 [in]要擷取的位元組數目 (`data`陣列必須包含至少此數目的位元組)。  
  
 `sizeGotten`  
 [out]傳回實際擷取的位元組的數目。  
  
 `data`  
 [in、 out]會利用所要求的資料填入的陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 建議的使用這個方法是在本機的陣列，擷取所有資料位元組，因為沒有任何方法可以略過在擷取處理序中的位元組。 在此情況下，參數`dataSize`應該所傳回的值[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)