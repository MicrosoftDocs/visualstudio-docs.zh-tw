---
title: 錯誤：請確認 DNS 都在目標電腦上正確設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c538a2b4ff4a50cd89bd9571a8746ccb58aaed04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850885"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>錯誤：確認目標電腦上的 DNS 設定都正確
您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 當目標電腦無法解析 Visual Studio 偵錯工具主機電腦的名稱時，便會發生這個錯誤。 請檢查目標電腦上的 DNS 設定。

- 如需檢視在 Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008 或 Windows Server 2008 R2 上 DNS 的設定資訊，請執行下列作業：在 [開始] 功能表上，選擇 [說明及支援]，然後搜尋 [變更 TCP/IP] 設定。

- 如需詳細資訊，請移至[Microsoft Windows 網站](http://go.microsoft.com/fwlink/?LinkId=252720)並搜尋**變更 TCP/IP 設定**。

  如果無法解決 DNS 問題，您可以嘗試用其他帳戶執行 [遠端偵錯工具]。 只有在您使用本機系統或網路服務帳戶執行 [遠端偵錯工具] 時，才會發生這個錯誤。 如果是以其他帳戶執行 [遠端偵錯工具]，就可以使用不需要 DNS 的 NTLM 驗證。 。 程序，請參閱[錯誤：在目標電腦上的 Visual Studio 遠端偵錯工具服務無法連回這部電腦](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)。
