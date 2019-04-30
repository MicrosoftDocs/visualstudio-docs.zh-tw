---
title: 錯誤：尚未安裝 ASP.NET |Microsoft Docs
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
ms.openlocfilehash: 98db3475c7d83427eb516f696731a738e34bd7a1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399295"
---
# <a name="error-aspnet-not-installed"></a>錯誤：尚未安裝 ASP.NET
當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 時，就會發生這個錯誤。 這可能表示從未安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，或是先安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 之後才安裝 IIS。

### <a name="to-reinstall-aspnet"></a>若要重新安裝 ASP.NET

1. 從 [命令提示字元] 視窗，執行下列命令：

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    何處*版本*代表安裝在您的電腦，例如 v1.0.370 上的.NET framework 的版本號碼。 您可以判斷的 framework 版本尋找`\WINDOWS\Microsoft.NET\Framework`目錄。

   > [!NOTE]
   > 您可以利用 Windows Server 2003 控制台中的 [新增或移除程式] 來安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
