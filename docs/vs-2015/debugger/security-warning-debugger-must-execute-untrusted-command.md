---
title: 安全性警告：偵錯工具必須執行未受信任的命令 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a29ba026f9b3c2b8839d474c2d0833eb79f7ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683290"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Security Warning: Debugger Must Execute Untrusted Command
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這個警告對話方塊會在您使用來源伺服器時出現。 它會指出，偵錯工具需要執行以取得原始程式碼的命令不在 srcsvr.ini 檔中所包含來源伺服器的受信任命令清單中。 如果這是有效的命令，您可將它加入至 srcsvr.ini 檔。 否則，您不應該執行該命令。 如需詳細資訊，請參閱 [指定符號 ( .pdb) 和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔。  
  
## <a name="message-text"></a>訊息文字  
 **偵錯工具必須執行下列未受信任的命令，才能從來源伺服器取得原始程式碼。**  
  
 **如果偵錯符號檔 (\*.pdb) 不是來自已知且受信任的來源，這個命令可能無效，或者執行這個命令會帶來危險。**  
  
 **要執行這個命令嗎?**  
  
## <a name="uielement-list"></a>UIElement 清單  
 文字方塊  
 來自 .pdb 檔案要執行的命令。  
  
 執行  
 允許命令執行。  
  
 不執行  
 停止執行命令並停止從來源伺服器下載檔案。  
  
## <a name="see-also"></a>另請參閱  
 [指定符號 ( .pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [來源伺服器](https://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
