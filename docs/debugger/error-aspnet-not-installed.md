---
title: "錯誤: 尚未安裝 ASP.NET |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: 36930db142821b11ed83edf846ccd3f65fd81d1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="error-aspnet-not-installed"></a>錯誤：尚未安裝 ASP.NET
當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 時，就會發生這個錯誤。 這可能表示從未安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，或是先安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 之後才安裝 IIS。  
  
### <a name="to-reinstall-aspnet"></a>若要重新安裝 ASP.NET  
  
1.  從 [命令提示字元] 視窗，執行下列命令：  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     其中*版本*代表您的電腦，例如 v1.0.370 上安裝.NET Framework 的版本號碼。 您可以判斷的 framework 版本中尋找`\WINDOWS\Microsoft.NET\Framework`目錄。  
  
    > [!NOTE]
    >  您可以使用 Windows Server 2003，安裝[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]使用**新增或移除程式**控制台 中。  
  
## <a name="see-also"></a>請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)