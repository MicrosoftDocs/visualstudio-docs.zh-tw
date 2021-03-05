---
description: 當您嘗試要進行偵錯工具的電腦上未正確安裝 ASP.NET 時，就會發生此錯誤。
title: 尚未安裝 ASP.NET
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 205f0fb3948414ec87b735af9b1b97917872a950
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147051"
---
# <a name="error-aspnet-not-installed"></a>錯誤：尚未安裝 ASP.NET
當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 時，就會發生這個錯誤。 這可能表示從未安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，或是先安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 之後才安裝 IIS。

### <a name="to-reinstall-aspnet"></a>若要重新安裝 ASP.NET

1. 從 [命令提示字元] 視窗，執行下列命令：

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    其中 *version* 代表電腦上所安裝之 .net Framework 的版本號碼，例如 v 1.0.370。 您可以藉由查看目錄來判斷架構版本 `\WINDOWS\Microsoft.NET\Framework` 。

   > [!NOTE]
   > 您可以利用 Windows Server 2003 控制台中的 [新增或移除程式] 來安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
