---
title: 錯誤：未安裝 ASP.NET |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839142"
---
# <a name="error-aspnet-not-installed"></a>錯誤：尚未安裝 ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 時，就會發生這個錯誤。 這可能表示從未安裝 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]，或是先安裝 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 之後才安裝 IIS。  
  
### <a name="to-reinstall-aspnet"></a>若要重新安裝 ASP.NET  
  
1. 從 [命令提示字元] 視窗，執行下列命令：  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     其中 *version* 代表電腦上所安裝之 .NET Framework 的版本號碼，例如 v 1.0.370。 您可以藉由查看目錄來判斷架構版本 `\WINDOWS\Microsoft.NET\Framework` 。  
  
    > [!NOTE]
    > 您可以利用 Windows Server 2003 控制台中的 [新增或移除程式]**** 來安裝 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
