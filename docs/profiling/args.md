---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 036b13a7fea5d64e23e2b7d5ccbd8a7b17f91176
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777046"
---
# <a name="args"></a>Args
VSPerfCmd.exe **Args** 選項指定要傳遞至 **Launch** 子命令的目標應用程式的引數清單。

 只有在命令列上也指定 **Launch** 時，才能使用 **Args**。 指定 **Launch** 時，**Args**為選擇性。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>參數
 `Arguments` **Launch** 命令的目標應用程式引數清單。

## <a name="required-options"></a>必要選項
 **Launch:**`AppName` 啟動指定的應用程式，並使用取樣方法開始分析。

## <a name="example"></a>範例
 下列範例使用 **Args** 選項將引數傳遞至 TestApp.exe。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)