---
title: IEEDataStorage::GetSize |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ee3e04c16b59ae97b93a3c521aa1a63f57835eb4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
傳回這個物件中包含的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```csharp  
int GetSize(  
   out uint size  
);  
```  
  
#### <a name="parameters"></a>參數  
 `size`  
 [out]此物件包含的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 使用[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)方法來擷取實際的資料位元組。  
  
## <a name="see-also"></a>請參閱  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)