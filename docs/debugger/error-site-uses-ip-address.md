---
title: 網站使用 IP 位址 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d574a10ba081a30f88583e035a18869e68976d18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871347"
---
# <a name="error-site-uses-ip-address"></a>錯誤：站台使用 IP 位址
當偵錯工具嘗試自動附加至使用 IP 位址的 Web 應用程式時，就會發生這個錯誤。 如果在 IIS 中將 [網站識別] 變更為 [使用特定 IP 位址]，就會發生這個問題。

 若要讓自動附加順利運作，您需要使用特定 IP 位址建立專案，而不是只有電腦名稱。 否則，偵錯工具會將電腦名稱變更為 localhost，導致無法將偵錯動詞命令傳送到 IIS。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 改用手動附加 (從 [偵錯] 功能表中選擇 [附加至處理序])。

     – 或 –

2. 變更 [IIS 網站識別] 設定。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)