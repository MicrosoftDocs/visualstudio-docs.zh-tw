---
title: 如何： 尋找 ASP.NET 處理序的名稱 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 899860baf5461eb798341cebf775ccde488915b7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473815"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>如何：尋找 ASP.NET 處理序的名稱
若要附加至執行中的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式，您必須知道 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序的名稱：  

-   如果您在 IIS 或 iis Express 上執行 ASP.NET Core，處理序名稱是 dotnet.exe。

-   如果您稍後會執行 ASP.NET IIS 6.0 上，則名稱是 w3wp.exe。  
  
-   如果您在舊版 IIS 上執行 ASP.NET，則名稱是 aspnet_wp.exe。

-   如果您在 iis Express 上執行 ASP.NET，則名稱會是 iisexpress.exe。
  
使用 Visual Studio 2012 之前的 Visual Studio 版本所建置的應用程式的[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]程式碼可位於檔案系統，並在 WebDev.WebServer.exe 測試伺服器或 WebDev.WebServer40.exe 之下執行。 在此情況下，您必須附加至 WebDev.WebServer.exe 或而不是 WebDev.WebServer40.exe[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]程序。 本案例僅適用於本機偵錯。
  
舊版 ASP 應用程式會在它們以同處理序 (In-Process) 方式執行時，於 IIS 處理序 inetinfo.exe 中執行。  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>若要判斷應用程式在哪一個 IIS 版本下執行  

1.  請確定應用程式正在執行，然後，從 Visual Studio 中，使用[附加至處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)命令。

2.  輸入的處理序名稱，例如 w3wp.exe 來快速找出處理程序中的第一個字母**可用的處理序**清單。

    本主題中的清單從可用的處理序會指示的 IIS 版本可用，以及哪些處理序正在執行您的應用程式。

    > [!NOTE]
    > 從 Visual Studio 2017 開始，您可以使用 [搜尋] 方塊來搜尋處理序名稱。
  
## <a name="see-also"></a>另請參閱  
 [附加至執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [遠端偵錯 Web 應用程式的必要條件](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [系統需求](../debugger/aspnet-debugging-system-requirements.md)   
 [偵錯 ASP.NET 應用程式](../debugger/how-to-enable-debugging-for-aspnet-applications.md)