---
title: Console | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74a5cecbdf3bba942c888a5cde3d49236047f4ee
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607872"
---
# <a name="console"></a>主控台
VSPerfCmd.exe **Console** 選項會在新的命令提示字元視窗中啟動指定的應用程式。 **Console** 只能與 VSPerfCmd **Launch** 選項搭配使用。 如果應用程式不是命令列應用程式，則 **Console** 沒有任何作用。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>參數
 無

## <a name="required-options"></a>必要選項
 **Console** 只能指定於也包含 **Launch** 選項的命令列。

 **Launch:**`AppName` 啟動分析工具及 `AppName` 指定的應用程式。

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)