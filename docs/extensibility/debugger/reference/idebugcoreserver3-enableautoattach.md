---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: e3b398e69db2cd16e9f8f277265ac100e48e7681
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Enables automatic attaching for the specified debug engines.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```cs  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `rgguidSpecificEngines`  
 [in] Array of GUIDs for each debug engine to mark as auto-attaching.  
  
 `celtSpecificEngines`  
 [in] The number of engines specified in `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] The starting URL to use when auto-attaching.  
  
 `pbstrSessionID`  
 [out] ID of the session that was auto-attached.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise returns error code. One error code is `E_AUTO_ATTACH_NOT_REGISTERED`, which indicates that the auto-attach class factory has not been registered.  
  
## <a name="remarks"></a>Remarks  
 When a program associated with the specified URL is started, the specified debug engines are automatically started and attached.  
  
## <a name="see-also"></a>See Also  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
