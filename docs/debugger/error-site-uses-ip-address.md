---
title: 錯誤：站台使用 IP 位址 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66e63a85ecbf42d0d4091a7ce9315c91184078ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871365"
---
# <a name="error-site-uses-ip-address"></a>錯誤：網站使用 IP 位址
當偵錯工具嘗試自動附加至使用 IP 位址的 Web 應用程式時，就會發生這個錯誤。 如果在 IIS 中將 [網站識別] 變更為 [使用特定 IP 位址]，就會發生這個問題。  
  
 若要讓自動附加順利運作，您需要使用特定 IP 位址建立專案，而不是只有電腦名稱。 否則，偵錯工具會將電腦名稱變更為 localhost，導致無法將偵錯動詞命令傳送到 IIS。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  改用手動附加 (從 [偵錯] 功能表中選擇 [附加至處理序])。  
  
     -或-  
  
2.  變更 [IIS 網站識別] 設定。  
  
## <a name="see-also"></a>請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)