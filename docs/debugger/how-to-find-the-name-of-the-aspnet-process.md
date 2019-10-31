---
title: 尋找正在執行的 ASP.NET 流程 |Microsoft Docs
ms.date: 11/04/2018
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187652"
---
# <a name="find-the-name-of-the-aspnet-process"></a>尋找 ASP.NET 處理序的名稱

若要對執行中的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式進行 debug，Visual Studio 偵錯工具必須依名稱附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 進程。

**若要找出哪個進程正在執行 ASP.NET 應用程式：**

1. 在執行應用程式的 Visual Studio 中，選取 [ **Debug** > **附加至進程**]。

1. 在 [**附加至進程**] 對話方塊中，輸入下列清單中處理常式名稱的前幾個字母，或在 [搜尋] 方塊中輸入。 正在執行的是執行 ASP.NET 應用程式的帳戶。 附加至該進程以對應用程式進行 debug。

    - *w3wp.exe*是 IIS 6.0 和更新版本。
    - *aspnet_wp.exe*是舊版的 IIS。
    - *iisexpress*是 iisexpress。
    - ASP.NET Core *dotnet* 。
    - *inetinfo*是執行同進程的舊版 ASP 應用程式。

>[!NOTE]
>Visual Studio 2012 和舊版的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式碼可以位於檔案系統上，並在測試伺服器*webdev.webserver.exe*或*webdev.webserver.exe*上執行。 在此情況下，若要進行本機的偵錯工具，請附加至*webdev.webserver.exe*或*webdev.webserver.exe* ，而不是 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 進程。

**另請參閱：**

- [附加至執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [遠端偵錯程式 web 應用程式的必要條件](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [系統需求](../debugger/aspnet-debugging-system-requirements.md)
- [對 ASP.NET 應用程式進行偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)