---
title: QueryCounters | Microsoft Docs
description: 瞭解 QueryCounters 選項如何列出電腦上可用的 CPU (硬體) 效能計數器。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d33b6fe42f786218bf78825a356a25edff2b31ae
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720432"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** 選項會列出電腦可用的 CPU (硬體) 效能計數器。

 **QueryCounters** 必須是命令列上唯一的選項。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>參數
 None

## <a name="remarks"></a>備註
 當您使用檢測方法時，分析工具可以收集每個資料集合事件的一或多個 CPU 效能計數器的值。 當您使用取樣分析方法時，您可以指定一個計數器事件和事件發生次數，用做取樣間隔。

 不同的處理器會公開不同的 CPU 效能計數器。 分析工具會定義一組幾乎所有處理器都可使用的一般計數器。 [QueryCounters] 選項會列出一般計數器名稱和處理器專用計數器名稱。

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
