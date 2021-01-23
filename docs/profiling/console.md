---
title: Console | Microsoft Docs
description: 使用 VSPerfCmd.exe 的主控台選項，在新的 [命令提示字元] 視窗中啟動指定的應用程式。 您必須將它與啟動選項搭配使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93c39bfb503bec9858e33b7acf04e0f0433264b9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720900"
---
# <a name="console"></a>主控台
VSPerfCmd.exe **Console** 選項會在新的命令提示字元視窗中啟動指定的應用程式。 **Console** 只能與 VSPerfCmd **Launch** 選項搭配使用。 如果應用程式不是命令列應用程式，則 **Console** 沒有任何作用。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>參數
 None

## <a name="required-options"></a>必要選項
 **Console** 只能指定於也包含 **Launch** 選項的命令列。

 **啟動：** `AppName` 啟動分析工具和指定的應用程式 `AppName` 。

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
