---
title: WaitStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17e4b8a2aac1ae2eac20fb7579977df66ee9caa7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937997"
---
# <a name="waitstart"></a>WaitStart
WaitStart 選項會導致 *VSPerfCmd.exe* Start 子命令僅在分析工具已初始化時，或者超過指定秒數時才返回。 根據預設，Start 命令會立即返回。 如果 Start 子命令返回而沒有初始化分析工具，則會傳回錯誤。 如果未指定秒數，Start 命令就會無限期等待。  
  
 WaitStart 選項適合批次檔使用，以確保分析工具已經初始化。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>參數  
 `Seconds`  
 從 Start 子命令返回之前要等待的秒數。  
  
## <a name="required-options"></a>必要選項  
 WaitStart 選項只能搭配 Start 子命令使用。  
  
 **Output:** `filename`  
 指定輸出檔名稱。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 在此批次檔範例中，Start 命令會等待 5 秒讓分析工具初始化。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```