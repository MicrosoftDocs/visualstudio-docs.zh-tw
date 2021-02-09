---
title: 指定要用於偵錯工具的 .NET Framework 版本 |Microsoft Docs
description: 指定用於偵錯工具的舊版 .NET Framework 版本。 Visual Studio 偵錯工具支援 .NET Framework 的舊版本和目前版本的偵錯工具。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 197cd51d31729119d48e255d038ad2e53f17a891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908369"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>指定舊版的 .NET Framework 版本以進行偵錯工具 (c #、Visual Basic、F # ) 

Visual Studio 偵錯工具支援舊版的 Microsoft .NET Framework 和目前版本的偵錯工具。 如果您從 Visual Studio 啟動應用程式，偵錯工具一律可以針對您正在進行的應用程式識別正確的 .NET Framework 版本。 但是，如果應用程式已經在執行中，而且您使用 [ **附加至**] 開始進行偵錯工具，則偵錯工具可能不一定能夠識別舊版 .NET Framework。 如果發生這種情況，就會出現錯誤訊息：

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

在出現這個錯誤的罕見情況下，您可以設定登錄機碼，以向偵錯工具表示要使用的版本。

### <a name="to-specify-a-net-framework-version-for-debugging"></a>若要指定偵錯的 .NET Framework 版本

1. 查詢目錄 Windows\Microsoft.NET\Framework 以尋找電腦上已安裝的 .NET Framework 版本。 版本號碼看起來如下所示：

    `V1.1.4322`

    識別正確的版本編號然後記下來。

2. 啟動 [登錄編輯程式] (regedit)。

3. 在 [登錄編輯程式] 中開啟 HKEY_LOCAL_MACHINE 資料夾。

4. 巡覽至：HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    如果此機碼不存在，請以滑鼠右鍵按一下 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine，然後按一下 [新增機碼]。 命名新的金鑰 `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` 。

5. 在巡覽至 {449EC4CC-30D2-4032-9256-EE18EB41B62B} 後，查詢 [名稱] 欄位然後尋找 CLRVersionForDebugging 機碼。

   1. 如果機碼不存在，請以滑鼠右鍵按一下 {449EC4CC-30D2-4032-9256-EE18EB41B62B}，然後按一下 [新增字串值]。 然後以滑鼠右鍵按一下新的字串值，按一下 [ **重新命名**]，然後輸入 `CLRVersionForDebugging` 。

6. 按兩下 [CLRVersionForDebugging]。

7. 在 [編輯字串] 方塊的 [值] 方塊中鍵入 .NET Framework 版本號碼。 例如：V1.1.4322。

8. 按一下 [確定]  。

9. 關閉 **登錄編輯程式**。

     如果在開始偵錯時仍然出現錯誤訊息，請確認已經在登錄中正確輸入版本編號。 也請確認您使用的是 Visual Studio 支援的 .NET Framework 版本。 偵錯工具與 .NET Framework 的最新版本和舊版相容，但是不一定與未來的版本相容。

## <a name="see-also"></a>另請參閱
- [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)