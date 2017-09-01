---
title: User (VSPerfCmd) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 7c87490f8e4ad01df8761ebb2afee0b2d3744fe2
ms.openlocfilehash: 4fbb8ad36461f3f06abb9318e537868e26d55860
ms.contentlocale: zh-tw
ms.lasthandoff: 08/31/2017

---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
The **User** option specifies the domain and user name of the account that owns the profiled process. This option is required only if the process is running as a user other than the logged on user. The process owner is listed in the User Name column on the Processes tab of Windows Task Manager.  
  
 The **User** option can only be specified on a command line that also contains the **Start** option.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parameters  
 `Domain`  
 The name of the user's domain.  
  
 `UserName`  
 The name of the user.  
  
## <a name="required-options"></a>Required Options  
 The **User** option can only be used with the **Start** option.  
  
 **Start:** `Method`  
 Initializes the profiler to the specified profiling method.  
  
## <a name="example"></a>Example  
 The following example demonstrates the use of the **User** option.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>See Also  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiling Stand-Alone Applications](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiling ASP.NET Web Applications](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiling Services](../profiling/command-line-profiling-of-services.md)
