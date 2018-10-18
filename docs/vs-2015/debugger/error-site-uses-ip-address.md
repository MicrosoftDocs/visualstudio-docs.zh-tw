---
title: 錯誤： 站台使用 IP 位址 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62d975903bc29835cbf43a21e38fe727a37aec9c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306354"
---
# <a name="error-site-uses-ip-address"></a>錯誤：站台使用 IP 位址
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當偵錯工具嘗試自動附加至使用 IP 位址的 Web 應用程式時，就會發生這個錯誤。 如果您變更，發生這種的情況**網站識別**要**使用特定的 IP 位址**在 IIS 中。  
  
 若要讓自動附加順利運作，您需要使用特定 IP 位址建立專案，而不是只有電腦名稱。 否則，偵錯工具會將電腦名稱變更為 localhost，導致無法將偵錯動詞命令傳送到 IIS。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  使用手動附加，而是 (從 [偵錯] 功能表中，選擇**附加至處理序**)。  
  
     -或-  
  
2.  變更**IIS 網站識別**設定。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



