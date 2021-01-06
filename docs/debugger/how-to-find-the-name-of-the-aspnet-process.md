---
title: 尋找正在執行的 ASP.NET 流程 |Microsoft Docs
description: 瞭解如何對執行中的 ASP.NET 應用程式進行 debug 錯。 您可以依名稱將 Visual Studio 偵錯工具附加至 ASP.NET 進程。
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: how-to
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
ms.openlocfilehash: 07d692dac1b5770cdee4682af5184649471c2828
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903437"
---
# <a name="find-the-name-of-the-aspnet-process"></a>尋找 ASP.NET 處理序的名稱

若要對執行 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 中的應用程式進行偵錯工具，Visual Studio 偵錯工具必須 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 依名稱附加至進程。

**若要找出正在執行 ASP.NET 應用程式的進程：**

1. 當應用程式執行時，在 Visual Studio 中，選取 [ **Debug**  >  **附加至進程**]。

1. 在 [ **附加至進程** ] 對話方塊中，從下列清單輸入進程名稱的第一個字母，或在 [搜尋] 方塊中輸入。 正在執行的應用程式是執行 ASP.NET 應用程式的那個。 附加至該進程以進行應用程式的偵錯工具。

    - *w3wp.exe* 是 IIS 6.0 和更新版本。
    - *aspnet_wp.exe* 是較早的 IIS 版本。
    - *iisexpress.exe* 為 IISExpress。
    - *dotnet.exe* 是 ASP.NET Core。
    - *inetinfo.exe* 是執行同進程的較舊 ASP 應用程式。

>[!NOTE]
>Visual Studio 2012 和先前的程式 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 代碼可位於檔案系統上，並在測試伺服器上執行 *WebDev.WebServer.exe* 或 *WebDev.WebServer40.exe*。 在此情況下，若要進行本機調試，請附加至 *WebDev.WebServer.exe* 或 *WebDev.WebServer40.exe* ，而不是 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理常式。

**另請參閱：**

- [附加至執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [遠端偵錯程式 web 應用程式的必要條件](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [系統需求](../debugger/aspnet-debugging-system-requirements.md)
- [對 ASP.NET 應用程式進行偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)