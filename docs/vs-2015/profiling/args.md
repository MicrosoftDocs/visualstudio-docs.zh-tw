---
title: Args | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad83466a01b1a9dc1aea406d84d24b81f44458a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788663"
---
# <a name="args"></a>Args
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Args** 選項指定要傳遞至 **Launch** 子命令的目標應用程式的引數清單。  
  
 只有在命令列上也指定 **Launch** 時，才能使用 **Args**。 指定 **Launch** 時，**Args**為選擇性。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>參數  
 `Arguments`  
 **Launch** 命令的目標應用程式的引數清單。  
  
## <a name="required-options"></a>必要選項  
 **Launch：** `AppName`  
 啟動指定的應用程式，並使用取樣方法開始程式碼剖析。  
  
## <a name="example"></a>範例  
 下列範例使用 **Args** 選項將引數傳遞至 TestApp.exe。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)



