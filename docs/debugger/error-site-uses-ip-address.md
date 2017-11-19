---
title: "錯誤： 站台使用 IP 位址 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e1ee3e2ed3d6524749757806931fbb8c4b9a36a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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