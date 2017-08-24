---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
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
ms.openlocfilehash: b27e475efefab9fe7deb0a3f9fc0b067448062bb
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Gets the title, friendly name, or file name of the hosting process of this program.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```cs  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `dwType`  
 [in] A value from the [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeration.  
  
 `pbstrHostName`  
 [out] Returns the requested name of the hosting process.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 In a typical implementation of this method, the `dwType` parameter is ignored and a friendly name of the host machine is returned. Another possible implementation is to pass the `dwType` parameter to a call to the [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) method to get the name.  
  
## <a name="see-also"></a>See Also  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
