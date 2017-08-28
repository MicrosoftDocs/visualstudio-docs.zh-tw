---
title: SccCloseProject Function | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
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
ms.openlocfilehash: bcdc0cbc2916c9efa6224a26abae94b75832c33a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="scccloseproject-function"></a>SccCloseProject Function
This function closes a project, marking the end of a particular session.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 pvContext  
 The source control plug-in context structure.  
  
## <a name="return-value"></a>Return Value  
 The source control plug-in implementation of this function is expected to return one of the following values:  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|The project was successfully closed.|  
|SCC_E_PROJNOTOPEN|No project is currently open.|  
|SCC_E_NOTAUTHORIZED|The user is not allowed to perform this operation.|  
|SCC_E_NONSPECIFICERROR|Nonspecific failure.|  
  
## <a name="remarks"></a>Remarks  
 The [SccOpenProject](../extensibility/sccopenproject-function.md) is always called before this function. A call to this function is then followed by a call to either the `SccOpenProject` function or the [SccUninitialize](../extensibility/sccuninitialize-function.md), which ends the connection to the source control system completely.  
  
## <a name="see-also"></a>See Also  
 [Source Control Plug-in API Functions](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
