---
title: TargetCLR | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145614"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**TargetCLR** 選項指定當應用程式載入多個 CLR 版本時要分析的 Common Language Runtime (CLR) 版本。  
  
 根據預設，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具以應用程式載入的第一個 CLR 版本為目標。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>參數  
 `ClrVersion`  
 CLR 的版本號碼。 使用版本格式 **vN.N.NNNNN**。  
  
## <a name="required-options"></a>必要選項  
 **TargetCLR** 選項僅能與 [啟動]  或 [附加]  選項一起使用。  
  
 **Launch：** `AppName`  
 啟動指定的應用程式並開始分析。  
  
 **Attach:** `PID`  
 開始分析指定的處理序。  
  
## <a name="example"></a>範例  
 本例使用 TargetCLR 選項確定分析的 CLR 版本是 4.0.11003。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
