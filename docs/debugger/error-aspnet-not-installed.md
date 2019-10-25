---
title: 錯誤： ASP.NET 未安裝 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 7d754cc2bb7931cdcbdb42abeddd554390ba320c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737911"
---
# <a name="error-aspnet-not-installed"></a>錯誤：尚未安裝 ASP.NET
當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 時，就會發生這個錯誤。 這可能表示從未安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，或是先安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 之後才安裝 IIS。

### <a name="to-reinstall-aspnet"></a>若要重新安裝 ASP.NET

1. 從 [命令提示字元] 視窗，執行下列命令：

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    其中*version*代表安裝在您電腦上之 .NET Framework 的版本號碼，例如 v 1.0.370。 您可以藉由查看 `\WINDOWS\Microsoft.NET\Framework` 目錄來判斷 framework 版本。

   > [!NOTE]
   > 您可以利用 Windows Server 2003 控制台中的 [新增或移除程式] 來安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。

## <a name="see-also"></a>請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
