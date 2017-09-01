---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
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
ms.openlocfilehash: 05ff3521879afe821fbac681a89ad993f5a18000
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Gets the dimensions of the array.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `dwCount`  
 [in] The number of dimensions to retrieve.  
  
 `dwDimensions`  
 [in, out] An array that is filled in with the sizes of each dimension. `dwCount` specifies the maximum size of the `dwDimensions` array.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 A multi-dimensional array can have different sizes for each dimension. For example, given the three-dimensional array `myarray[3][2][6]`, this method would return 3, 2, and 6 in the `dwDimensions` parameter in that order.  
  
## <a name="see-also"></a>See Also  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
