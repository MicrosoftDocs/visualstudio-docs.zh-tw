---
title: 錯誤： 站台使用 IP 位址 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: b726902c57cc95b694f2ab7e656a444ed42a0ba9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470900"
---
# <a name="error-site-uses-ip-address"></a>錯誤：站台使用 IP 位址
當偵錯工具嘗試自動附加至使用 IP 位址的 Web 應用程式時，就會發生這個錯誤。 如果您變更，發生這種的情況**網站識別**至**使用特定 IP 位址**在 IIS 中。  
  
 若要讓自動附加順利運作，您需要使用特定 IP 位址建立專案，而不是只有電腦名稱。 否則，偵錯工具會將電腦名稱變更為 localhost，導致無法將偵錯動詞命令傳送到 IIS。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  使用手動附加，而是 (從 偵錯 功能表中，選擇 **附加至處理序**)。  
  
     -或-  
  
2.  變更**IIS 網站識別**設定。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)