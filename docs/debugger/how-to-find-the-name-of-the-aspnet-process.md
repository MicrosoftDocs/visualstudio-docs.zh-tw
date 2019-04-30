---
title: 尋找執行的 ASP.NET 處理序 |Microsoft Docs
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
ms.openlocfilehash: 27221a4ae47b9fb06130b550ceb6d3cc1f00dce0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906800"
---
# <a name="find-the-name-of-the-aspnet-process"></a>尋找 ASP.NET 處理序的名稱

若要偵錯執行[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]應用程式，Visual Studio 偵錯工具必須附加至[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]處理程序名稱。

**若要找出哪些處理序正在執行 ASP.NET 應用程式：**

1. 使用應用程式執行，請在 Visual Studio 中，選取**偵錯** > **附加至處理序**。

1. 在 **附加至處理序**對話方塊中，輸入程序的第一個字母從下列清單中，名稱，或在搜尋方塊中輸入它們。 正在執行的一個就是執行 ASP.NET 應用程式。 將附加至處理序偵錯應用程式。

    - *w3wp.exe*是 IIS 6.0 和更新版本。
    - *aspnet_wp.exe*是舊版的 IIS。
    - *iisexpress.exe*是 IISExpress。
    - *dotnet.exe*是 ASP.NET Core。
    - *inetinfo.exe*是同處理序執行的舊版 ASP 應用程式。

>[!NOTE]
>Visual Studio 2012 及更早版本[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]程式碼可以在檔案系統和測試伺服器上執行*WebDev.WebServer.exe*或是*WebDev.WebServer40.exe*。 在此情況下，進行本機偵錯，附加至*WebDev.WebServer.exe*或是*WebDev.WebServer40.exe*而不是[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]程序。

**另請參閱：**

- [附加至執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [遠端偵錯的 web 應用程式的必要條件](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)
- [系統需求](../debugger/aspnet-debugging-system-requirements.md)
- [對 ASP.NET 應用程式進行偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)