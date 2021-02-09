---
title: Args | Microsoft Docs
description: 使用 VSPerfCmd.exe 的 ARGS 選項，將引數清單傳遞給啟動子命令的目標應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44e68822ebd444b8683b85b2df0c49b14d78bcaa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901067"
---
# <a name="args"></a>Args
VSPerfCmd.exe **Args** 選項指定要傳遞至 **Launch** 子命令的目標應用程式的引數清單。

 只有在命令列上也指定 **Launch** 時，才能使用 **Args**。 指定 **Launch** 時，**Args** 為選擇性。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>參數
 `Arguments`**啟動** 命令之目標應用程式的引數清單。

## <a name="required-options"></a>必要選項
 **啟動：** `AppName` 啟動指定的應用程式，並開始使用取樣方法進行程式碼剖析。

## <a name="example"></a>範例
 下列範例使用 **Args** 選項將引數傳遞至 TestApp.exe。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
