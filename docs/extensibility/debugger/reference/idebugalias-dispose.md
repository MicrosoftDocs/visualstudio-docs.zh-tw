---
title: IDebugAlias::Dispose | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 85880650b6385f11c8774421373bbf31f474961a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Marks this alias for removal.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Dispose();  
```  
  
```cs  
int Dispose();  
```  
  
#### <a name="parameters"></a>Parameters  
 None.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Once this method is called, the alias is no longer available.  
  
## <a name="see-also"></a>See Also  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
