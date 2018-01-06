---
title: "IPropertyProxyEESide::CreateReplacementObject |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords: IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 958b34ea15fdbfda4c98979fec3ce7210183d921
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
建立運算式評估工具 (EE) 的特定資料物件的複本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dataIn`  
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)保存要複製資料的物件。  
  
 `dataOut`  
 [out]傳回新`IEEDataStorage`物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法給予[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，表示為位元組陣列。 通常由 EE 不實作此連入的資料物件。 不過，這個方法所傳回的物件一律由 EE，它可讓 EE 實作`IEEDataStorage`上想要使用任何類別的介面。  
  
 請注意的資料提供傳入`IEEDataStorage`物件必須是相同的資料，在傳出`IEEDataStorage`物件。  
  
## <a name="see-also"></a>請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)