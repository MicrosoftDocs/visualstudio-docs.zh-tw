---
title: DA0029：不支援的 CLR 版本 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df5deda533c21033d26af4b8dc08d98a5dafc583
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484743"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029：不支援的 CLR 版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[DA0029： 不支援的 CLR 版本](https://docs.microsoft.com/visualstudio/profiling/da0029-unsupported-clr-version)。  
  
規則 Id |DA0029 |  
|類別目錄 |分析工具使用方式 |  
|程式碼剖析方法 |從命令列剖析 |  
|訊息 |在收集期間偵測到不受支援的 CLR 版本。 受控的符號可能無法正確解析。 |  
|規則類型 |資訊。 |  
  
## <a name="cause"></a>原因  
 您嘗試使用分析工具不支援的 [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] 來分析應用程式。  
  
## <a name="rule-description"></a>規則描述  
 因為分析工具無法解析應用程式中執行之 Managed 程式碼的符號，所以發生此警告。 分析工具無法解析執行 [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] 之應用程式的受控碼符號。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 無。



