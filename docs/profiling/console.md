---
title: Console | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04cf166880ac8bcf83d4657b9c1c2eec1b46a14a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34690812"
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
  
 **Launch：** `AppName`  
 啟動分析工具及 `AppName` 指定的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服務](../profiling/command-line-profiling-of-services.md)