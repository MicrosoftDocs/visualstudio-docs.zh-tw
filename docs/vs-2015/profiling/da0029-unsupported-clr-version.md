---
title: DA0029：不支援的 CLR 版本 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 6334fc69607f6d39e75d20c3b3ca228507db169d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265105"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029：不支援的 CLR 版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



