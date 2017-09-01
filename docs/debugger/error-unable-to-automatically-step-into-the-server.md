---
title: 'Error: Unable to Automatically Step Into the Server | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 9e6c28d42bec272c6fd6107b4baf0109ff29197e
ms.openlocfilehash: db04d4c3c25f5ac0d51f41a44cb78f32f1778ef5
ms.contentlocale: zh-tw
ms.lasthandoff: 08/22/2017

---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Error: Unable to Automatically Step Into the Server
The error reads:  
  
 Unable to Automatically Step Into the Server. The debugger was not notified before the remote procedure was executed  
  
 This error can occur when you are trying to step into a web service (see [Stepping Into an XML Web Service](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). It can occur whenever [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] is not set up properly.  
  
 Possible causes are:  
  
-   The web.config file for your [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application does not set debug to "true" in (see [Debug Mode in ASP.NET Applications](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   A version of [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] was installed after Visual Studio was installed. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] should be installed before Visual Studio. To fix this problem, use the Windows **Control Panel > Programs and Features** to repair your Visual Studio installation.  
  
## <a name="see-also"></a>See Also  
 [Remote Debugging Errors and Troubleshooting](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
