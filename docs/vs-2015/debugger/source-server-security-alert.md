---
title: 來源伺服器安全性警示 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 76d61520bf17ad3230a437c295de387a910f808f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938953"
---
# <a name="source-server-security-alert"></a>來源伺服器安全性警示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當使用來源伺服器時，僅限使用來自已知和受信任位置的符號檔。  
  
 這個警告會在您啟用來源伺服器支援時出現。 來源伺服器命令內嵌在偵錯符號檔 (PDB 檔) 中。 請確定您知道 PDB 檔的來源。  
  
> [!IMPORTANT]
>  下列潛在的安全性威脅使用來源伺服器時必須列入考量：任意命令可以內嵌在應用程式的 PDB 檔案，因此請確定您只將您想要在 srcsrv.ini 檔案中執行。 嘗試執行 srcsvr.ini 檔案中未包含的任何命令，都會讓確認對話方塊出現。 如需詳細資訊，請參閱[安全性警告：偵錯工具必須執行未受信任的命令](../debugger/security-warning-debugger-must-execute-untrusted-command.md)。對命令參數進行任何驗證，因此請謹慎使用受信任的命令。 例如，如果您信任 cmd.exe，惡意的使用者便可能指定會使命令具危險性的參數。  
  
## <a name="see-also"></a>另請參閱  
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [來源伺服器](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
