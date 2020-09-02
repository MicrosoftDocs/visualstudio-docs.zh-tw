---
title: DA0003：許多核心樣本 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad9a0671595d4628932ff4f2db41a137e060c4d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158716"
---
# <a name="da0003-many-kernel-samples"></a>DA0003：許多核心樣本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則識別碼 |DA0003 |  
|類別 |分析工具使用量 |  
|分析方法 |取樣 |  
|訊息 |在核心模式中有很高比例的樣本。 這可能指出大量 I/O 活動或較高的內容切換率。 請考慮使用檢測模式重新分析應用程式。|  
|規則類型 |資訊 |  
  
## <a name="cause"></a>原因  
 針對應用程式收集的大部分呼叫堆疊範例是以核心模式執行。 請考慮使用不同的分析方法來分析應用程式。  
  
## <a name="rule-description"></a>規則描述  
 在 Windows 中，您可以使用核心模式或使用者模式來執行程式碼   (核心模式也稱為「特殊許可權模式」。 ) 只有低層級的系統程式碼（例如設備磁碟機）才會以核心模式執行。 使用者模式應用程式可以轉換為核心模式以執行 I/O 作業、等候執行緒或處理序同步原始物件，或執行系統呼叫。  
  
 當您要分析將大部分時間都用在以使用者模式工作的分析應用程式時，取樣最為有效。 以核心模式執行應用程式時所收集的樣本數目可能指出經常執行的 I/O 作業，或可能指出正在發生內容參數。 無法使用取樣方法來調查其中任一項作業。 如果取得太多核心模式樣本，則取樣資料可能未包含足夠的使用者模式樣本來進行統計。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 請考慮使用下列其中一個選項重新分析應用程式：  
  
- 使用檢測方法進行分析。  
  
- 增加取樣率，嘗試以使用者模式收集更多的樣本。
