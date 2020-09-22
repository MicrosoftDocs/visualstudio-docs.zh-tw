---
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1c4138b1f3d102e235bb03ebcfd5a80808d8762c
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852793"
---
# <a name="error-aspnet-not-installed"></a>錯誤：尚未安裝 ASP.NET
當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 時，就會發生這個錯誤。 這可能表示從未安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，或是先安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 之後才安裝 IIS。

### <a name="to-reinstall-aspnet"></a>若要重新安裝 ASP.NET

1. 從 [命令提示字元] 視窗，執行下列命令：

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    其中 *version* 代表電腦上所安裝之 .NET Framework 的版本號碼，例如 v 1.0.370。 您可以藉由查看目錄來判斷架構版本 `\WINDOWS\Microsoft.NET\Framework` 。

   > [!NOTE]
   > 您可以利用 Windows Server 2003 控制台中的 [新增或移除程式]**** 來安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
