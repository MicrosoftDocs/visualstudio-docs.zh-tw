---
title: 來源伺服器安全性警示 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1bce9b20e6787ae6234ba308c29f512ba47986d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="source-server-security-alert"></a>來源伺服器安全性警示
當使用來源伺服器時，僅限使用來自已知和受信任位置的符號檔。  
  
 這個警告會在您啟用來源伺服器支援時出現。 來源伺服器命令內嵌在偵錯符號檔 (***.pdb**檔案)。 請確定您知道 PDB 檔的來源。  
  
> [!IMPORTANT]
>  使用來源伺服器時，請務必考量下列潛在安全性威脅：任意命令可能會內嵌於應用程式的 PDB 檔中，因此請確定只將想要執行的命令置於 srcsrv.ini 檔案中。 嘗試執行 srcsvr.ini 檔案中未包含的任何命令，都會讓確認對話方塊出現。 如需詳細資訊，請參閱 [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md)。 由於不會對命令參數進行任何驗證，因此請謹慎使用受信任的命令。 例如，如果您信任 cmd.exe，惡意的使用者便可能指定會使命令具危險性的參數。  
  
## <a name="see-also"></a>請參閱  
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [來源伺服器](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
