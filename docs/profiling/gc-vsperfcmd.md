---
title: GC (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45b93d3184a825c11e0a4742ad752c6a2c1c031e
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237561"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
**GC** 選項啟用 .NET Framework 記憶體配置和物件存留期資料的收集。 **GC** 選項只能與取樣分析方法搭配使用，並且只能與 **Launch** 選項搭配使用。  
  
 當您要使用 **GC** 選項時，不需要 VSPerfClrEnv **/sampleon** 命令。  
  
 如果未指定任何參數，或指定 **Allocation** 參數，則只會收集 .NET Framework 記憶體配置資料。 如果指定 **Lifetime** 參數，則會收集 .NET Framework 記憶體配置和 .NET Framework 物件存留期資料。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>參數  
 **配置**  
 預設值： 收集 .NET Framework 記憶體配置資料。  
  
 **存留期**  
 收集 .NET Framework 記憶體配置資料和 .NET Framework 物件存留期資料。  
  
## <a name="required-options"></a>必要選項  
 **GC** 選項只能與 **Launch** 選項搭配使用。  
  
 **Launch：** `AppName`  
 啟動指定的應用程式，並使用取樣方法開始程式碼剖析。  
  
## <a name="example"></a>範例  
 下列範例會啟動應用程式，並收集 .NET Framework 記憶體配置資料。  
  
```cmd  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服務](../profiling/command-line-profiling-of-services.md)