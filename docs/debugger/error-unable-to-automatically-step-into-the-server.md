---
title: 錯誤-無法自動逐步執行伺服器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 647f51314d5506e817fa6982aa693b62f62125cf
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599908"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>錯誤：無法自動逐步執行至伺服器
此錯誤指出：

 無法自動逐步執行至伺服器。 執行遠端程序之前，未通知偵錯工具。

 當您嘗試逐步執行 Web 服務 (請參閱 [逐步執行 XML Web Service](/previous-versions/zc57803s(v=vs.100))) 時，可能會發生這個錯誤。 一旦沒有正確設定 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ，便可能會發生這個錯誤。

 可能的原因包括：

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式的 web.config 檔沒有將偵錯設定為 "true" (請參閱 [ASP.NET 應用程式中的偵錯模式](../debugger/how-to-enable-debugging-for-aspnet-applications.md))。

- 在 Visual Studio 安裝之後，安裝了某個版本的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應該在 Visual Studio 之前安裝。 若要修正這個問題，請使用 Windows [控制台] > [程式和功能]**** 來修復 Visual Studio 安裝。

## <a name="see-also"></a>另請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [遠端偵錯](../debugger/remote-debugging.md)