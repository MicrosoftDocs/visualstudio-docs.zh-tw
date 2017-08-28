---
title: SccProperties Function | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
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
ms.openlocfilehash: ce333ce31ffb7f265677837dc7fc27b0ac502c0b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="sccproperties-function"></a>SccProperties Function
This function displays source control properties for a file or project.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 pvContext  
 [in] The source control plug-in context structure.  
  
 hWnd  
 [in] A handle to the IDE window that the source control plug-in can use as a parent for any dialog boxes that it provides.  
  
 lpFileName  
 [in] The fully qualified path name of the file or project.  
  
## <a name="return-value"></a>Return Value  
 The source control plug-in implementation of this function is expected to return one of the following values:  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Properties were successfully displayed.|  
|SCC_I_RELOADFILE|The version control system has modified the file properties, so the IDE should reload this file.|  
|SCC_E_PROJNOTOPEN|The specified project has not been opened in source control.|  
|SCC_E_NOTAUTHORIZED|The user is not authorized to view properties of this file or project.|  
|SCC_E_FILENOTCONTROLLED|The specified file or project is not under source control.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|An unknown or general error occurred.|  
  
## <a name="remarks"></a>Remarks  
 The source control plug-in displays the properties in its own dialog box.  
  
 The properties are defined by the source control plug-in and may differ from plug-in to plug-in. If the plug-in allows the user to change the source control properties of a file, it should return `SCC_I_RELOAD` to signal the IDE that this file or project needs to be reloaded.  
  
## <a name="see-also"></a>See Also  
 [Source Control Plug-in API Functions](../extensibility/source-control-plug-in-api-functions.md)
