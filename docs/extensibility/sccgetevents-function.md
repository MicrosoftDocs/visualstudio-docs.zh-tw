---
title: SccGetEvents Function | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
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
ms.openlocfilehash: 8db1e74d8529192408be12c9f87ca4f3ea086516
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="sccgetevents-function"></a>SccGetEvents Function
This function retrieves a queued status event.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 pvContext  
 [in] The source control plug-in context structure.  
  
 lpFileName  
 [in, out] Buffer where the source control plug-in puts the returned file name (up to _MAX_PATH characters).  
  
 lpStatus  
 [in, out] Returns status code (see [File Status Code](../extensibility/file-status-code-enumerator.md) for possible values).  
  
 pnEventsRemaining  
 [in, out] Returns number of entries left in the queue after this call. If this number is large, the caller may decide to call the [SccQueryInfo](../extensibility/sccqueryinfo-function.md) to get all the information at once.  
  
## <a name="return-value"></a>Return Value  
 The source control plug-in implementation of this function is expected to return one of the following values:  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Get events succeeded.|  
|SCC_E_OPNOTSUPPORTED|This function is not supported.|  
|SCC_E_NONSPECIFICERROR|Nonspecific failure.|  
  
## <a name="remarks"></a>Remarks  
 This function is called during idle processing to see if there have been any status updates for files under source control. The source control plug-in maintains status of all the files it knows about, and whenever a change of status is noted by the plug-in, the status and the associated file are stored in a queue. When `SccGetEvents` is called, the top element of the queue is retrieved and returned. This function is constrained to return only previously cached information and must have a very quick turnaround (that is, no reading of the disk or asking the source control system for status); otherwise the performance of the IDE may start to degrade.  
  
 If there is no status update to report, the source control plug-in stores an empty string in the buffer pointed to by `lpFileName`. Otherwise, the plug-in stores the full path name of the file for which the status information has changed and returns the appropriate status code (one of the values detailed in [File Status Code](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>See Also  
 [Source Control Plug-in API Functions](../extensibility/source-control-plug-in-api-functions.md)   
 [File Status Code](../extensibility/file-status-code-enumerator.md)
