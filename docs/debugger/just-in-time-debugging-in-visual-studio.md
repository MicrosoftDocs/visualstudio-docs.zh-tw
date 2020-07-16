---
title: 停用即時偵錯工具 |Microsoft Docs
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
ms.openlocfilehash: 3155c2cdc9ea3dc5208a52e5fe37f697a4ad5ef6
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386117"
---
# <a name="disable-the-just-in-time-debugger"></a>停用 Just-In-Time 偵錯工具

當執行中的應用程式發生錯誤，並防止應用程式繼續執行時，[即時偵錯工具] 對話方塊可能會開啟。

即時偵錯工具可讓您選擇啟動 Visual Studio 來進行錯誤的偵測。 您必須安裝 Visual Studio 或另一個已選取的偵錯工具，才能查看錯誤的詳細資訊，或嘗試進行調試。

如果您已經是 Visual Studio 使用者，而且想要嘗試進行錯誤的檢查，請參閱[使用即時偵錯工具進行 debug](../debugger/debug-using-the-just-in-time-debugger.md)。 如果您無法修正錯誤，或想要讓即時偵錯工具無法開啟，您可以[從 Visual Studio 停](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)用即時的偵測。

如果您已安裝 Visual Studio，但不再這麼做，您可能需要[從 Windows 登錄中停用即時的調試](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)。

如果您尚未安裝 Visual Studio，您可以停用腳本的偵錯工具或伺服器端的偵錯工具，以避免即時的偵測。

- 如果您正嘗試執行 web 應用程式，請停用腳本的偵錯工具：

  在 [Windows**控制台**] 的 [  >  **網路和網際網路**  >  **網際網路選項**] 中，選取 [**停用腳本調試（Internet Explorer）** ] 和 **[停用腳本調試（其他）**]。 確切的步驟和設定取決於您的 Windows 版本與瀏覽器。

  ![JIT 網際網路選項](../debugger/media/jitinternetoptions.png "JIT 網際網路選項")

- 如果您是在 IIS 中裝載 ASP.NET web 應用程式，請停用伺服器端的偵錯工具：

  1. 在 [IIS 管理員**功能] 視圖**的 [ **ASP.NET** ] 區段下，按兩下 [ **.net 編譯**]，或選取它，然後選取 [**動作**] 窗格中的 [**開啟功能**]。
  1. 在 [**行為**  >  **Debug**] 底下，選取 [ **False**]。 較舊版本的 IIS 中的步驟不同。

停用即時偵測之後，應用程式可能可以處理錯誤並正常執行。

如果應用程式仍有未處理的錯誤，您可能會看到錯誤訊息，或是應用程式可能當機或停止回應。 在錯誤修正之前，應用程式將無法正常執行。 您可以嘗試聯絡應用程式的擁有者，並要求他們加以修正。
