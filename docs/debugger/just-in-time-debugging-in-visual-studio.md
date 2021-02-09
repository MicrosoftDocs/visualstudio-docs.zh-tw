---
title: 停用即時偵錯工具 |Microsoft Docs
description: 當應用程式中發生錯誤時，即時偵錯工具對話方塊可能會開啟。 瞭解發生此情況時可執行檔動作，以及防止它的方法。
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670809ea2c9ef04107dbec5634f40831b68b94c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931496"
---
# <a name="disable-the-just-in-time-debugger"></a>停用 Just-In-Time 偵錯工具

當執行中的應用程式發生錯誤時，即時偵錯工具對話方塊可能會開啟，並防止應用程式繼續進行。

即時偵錯工具可讓您選擇啟動 Visual Studio 來偵測錯誤。 您必須已安裝 Visual Studio 或另一個選取的偵錯工具，才能查看錯誤的詳細資訊，或嘗試將其進行調試。

如果您已經是 Visual Studio 使用者，而且想要嘗試進行錯誤的偵測，請參閱 [使用即時偵錯工具](../debugger/debug-using-the-just-in-time-debugger.md)來進行 debug。 如果您無法修正錯誤，或想要讓即時偵錯工具保持開啟，您可以 [從 Visual Studio 停用即時調試](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)程式。

如果您已安裝 Visual Studio 但不再這麼做，您可能需要 [從 Windows 登錄中停用即時調試](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)。

如果您未安裝 Visual Studio，可以停用腳本的偵錯工具或伺服器端的偵錯工具，以防止即時偵錯工具。

- 如果您想要執行 web 應用程式，請停用腳本偵錯工具：

  在 [Windows **主控台**  >  **網路和網際網路**  >  **網際網路選項**] 中，選取 [**停用腳本調試] (Internet Explorer)** 並 **停用其他 (的腳本調試**。 確切的步驟和設定取決於您的 Windows 版本和您的瀏覽器。

  ![JIT 網際網路選項](../debugger/media/jitinternetoptions.png "JIT 網際網路選項")

- 如果您是在 IIS 中裝載 ASP.NET web 應用程式，請停用伺服器端的偵錯工具：

  1. 在 [IIS 管理員 **功能視圖**] 的 [ **ASP.NET** ] 區段下，按兩下 [ **.net 編譯**]，或選取它，然後選取 [**動作**] 窗格中的 [**開啟功能**]。
  1. 在 [**行為**  >  **Debug**] 底下，選取 [ **False**]。 較舊版本的 IIS 中的步驟不同。

停用即時偵錯工具之後，應用程式可能可以處理錯誤並正常執行。

如果應用程式仍有未處理的錯誤，您可能會看到錯誤訊息，或應用程式可能損毀或停止回應。 在錯誤修正之前，應用程式不會正常執行。 您可以嘗試與應用程式的擁有者聯繫，並要求他們加以修正。
