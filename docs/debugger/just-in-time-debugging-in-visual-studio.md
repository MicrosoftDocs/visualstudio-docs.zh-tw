---
title: 如何： 回應在 Just-in-time 偵錯工具 |Microsoft 文件
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c506e12fc8e6637e2b53852587e6a37c57cbf5ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>如何： 回應在 Just-in-time 偵錯工具

當您看到的時間只需時，您應該採取的動作取決於您嘗試進行的動作的偵錯工具 對話方塊：

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>如果您想要修正或偵錯 （Visual Studio 使用者）

- 您必須擁有[安裝 Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48146)來檢視有關錯誤的詳細的資訊，並再試一次進行偵錯。 如需詳細資訊，請參閱[使用 Just-In-Time 偵錯工具進行偵錯](../debugger/debug-using-the-just-in-time-debugger.md)。 如果您不能解決此錯誤並修正應用程式，請連絡應用程式的擁有者，以解決此錯誤。

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>如果您想要防止出現 [Just-In-Time 偵錯工具] 對話方塊

您可以採取步驟來阻止恰好時間出現的 [偵錯工具] 對話方塊。 如果應用程式會處理錯誤，您可以正常執行的應用程式。

1. （web 應用程式）如果您嘗試執行 web 應用程式，您可以停用指令碼偵錯。

    針對 Internet Explorer 或 Edge，停用 [網際網路選項] 對話方塊中的指令碼偵錯。 您可以存取這些設定從**控制台** > **網路和網際網路** > **網際網路選項**(的確切步驟取決於您版本的 Windows 和您的瀏覽器）。

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    然後重新開啟網頁上找到的錯誤。 如果變更此設定無法解決問題，請連絡 web 應用程式的擁有者可以修正這個問題。

3. （visual Studio 使用者）如果您已安裝的 Visual Studio （或如果您已安裝，且已經將它移除），[停用時間恰好偵錯](../debugger/debug-using-the-just-in-time-debugger.md)，然後再試一次執行應用程式。

    > [!IMPORTANT]
    > 如果您停用時間恰好偵錯和應用程式遇到未處理的例外狀況 （錯誤），相反地，您會看到標準錯誤對話方塊或應用程式會損毀，或停止回應。 錯誤修正 （由您或應用程式的擁有者） 之前，應用程式將無法正常執行。

2. （ASP.NET 和 IIS）如果您裝載在 IIS 中的 ASP.NET Web 應用程式，停用伺服器端偵錯。

    在 IIS 管理員 中，以滑鼠右鍵按一下伺服器節點，然後選擇 **切換到功能檢視**。 在 [ASP.NET] 區段中，選擇 **.NET 編譯**，並確定您選擇**False**做為偵錯行為 （步驟都在舊版 IIS 不同）。
  
## <a name="see-also"></a>另請參閱    
 [偵錯工具基礎](../debugger/debugger-basics.md)   
