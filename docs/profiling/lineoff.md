---
title: LineOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac671c3b0ba40c462403b2afa850c3936156d6d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774122"
---
# <a name="lineoff"></a>LineOff
根據預設，分析工具會在您使用取樣分析方法時，收集原始程式碼行號和位移資料行號。 VSPerfCmd 的 **LineOff** 選項在使用 VSPerfCmd 啟動應用程式時，會停用行號資料收集。 指定 [LineOff]**** 時，分析資料會收集至函式層級。

 **LineOff** 只能搭配 [啟動]**** 選項，而且只能在已初始化分析工具，使用 [啟動]****：[取樣]**** 選項進行取樣時。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>參數
 None

## <a name="required-options"></a>必要選項
 **LineOff** 選項只能用在包含 [啟動]**** 選項的命令列中。

 **啟動：**`AppName`啟動指定的應用程式並開始使用採樣方法進行分析。

## <a name="example"></a>範例
 這個範例會啟動應用程式和分析工具，並停用程式碼層級的取樣。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [設定檔ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
