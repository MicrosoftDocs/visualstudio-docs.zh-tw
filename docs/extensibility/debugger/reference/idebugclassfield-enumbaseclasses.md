---
title: IDebugClassField::EnumBaseClasses |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3f62f570b489427b59aefe8153692ab8f9fc2181
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
建立這個類別的基底類別的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表基底類別清單。 如果沒有基底類別，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，會傳回 S_OK，如果沒有基底類別會傳回 S_SH_NO_BASE_CLASSES (和`ppEnum`參數設定為 null 的值)，否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 中的列舉值物件的基底類別中最立即的 （或最常衍生的） 基底類別的大部分的遠端的基底類別的順序指定。 例如，如果已指定 c + + 類別：  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 列舉會傳回基底類別的順序`Level2`， `Level1`， `Root`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)