---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 6
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
ms.openlocfilehash: e9b83b5b507b266c860777007e79670d6beebfb9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Sets the service provider.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```cs  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pSP`  
 [in] Reference to the interface of the service provider.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 This method will be called before any other methods are called.  
  
## <a name="see-also"></a>See Also  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
