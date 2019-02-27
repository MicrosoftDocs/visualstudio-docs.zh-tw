---
title: 停用-Just-in-time 偵錯工具 |Microsoft Docs
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c848281a89213a216bd8ec3ac1e651b6dfc32e4
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796409"
---
# <a name="disable-the-just-in-time-debugger"></a>停用 Just-In-Time 偵錯工具

[Just-In-Time 偵錯工具] 對話方塊中可能會開啟執行中應用程式，發生錯誤時，並阻止應用程式繼續執行。

Just-In-Time 偵錯工具可讓您啟動 Visual Studio 偵錯錯誤的選項。 您必須擁有[Visual Studio](http://visualstudio.microsoft.com)或另一個所選安裝偵錯工具若要檢視有關錯誤的詳細的資訊，或嘗試進行偵錯。

如果您是 Visual Studio 使用者，而且想要嘗試偵錯錯誤，請參閱 <<c0> [ 使用 Just-In-Time 偵錯工具進行偵錯](../debugger/debug-using-the-just-in-time-debugger.md)。 如果您不能修正錯誤，或想要保留 Just-In-Time 偵錯工具無法開啟，您可以[從 Visual Studio 偵錯的停用 Just In Time](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)。

如果您已安裝 Visual Studio，但不是會再執行，您可能需要[停用 Just In Time 偵錯從 Windows 登錄](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)。

如果您沒有安裝 Visual Studio，您可以防止恰好時間偵錯的方式停用指令碼偵錯，或伺服器端偵錯。

- 如果您想要執行 web 應用程式，停用指令碼偵錯：

  在 Windows**控制台中** > **網路和網際網路** > **網際網路選項**，選取**停用指令碼偵錯 （Internet Explorer)** 並**停用指令碼除錯 （其他）**。 確切步驟和設定這需視您的 Windows 和您的瀏覽器版本而定。

  ![JIT 網際網路選項](../debugger/media/jitinternetoptions.png "JIT 網際網路選項")

- 如果您裝載在 IIS 中的 ASP.NET web 應用程式，停用伺服器端偵錯：

  1. 在 IIS 管理員**功能檢視**下方**ASP.NET**區段中，按兩下 **.NET 編譯**，或選取它，然後選取**開啟功能**中**動作**窗格。
  1. 底下**行為** > **偵錯**，選取**False**。 步驟是在舊版 IIS 中的不同。

停用 Just 時間偵錯之後，應用程式可以處理錯誤並正常執行。

如果應用程式仍有未處理的錯誤，您可能會看到錯誤訊息，或應用程式可能會當機或停止回應。 錯誤修正之前，不會正常執行的應用程式。 您可以嘗試連絡應用程式的擁有者，並要求他們要修正此問題。
