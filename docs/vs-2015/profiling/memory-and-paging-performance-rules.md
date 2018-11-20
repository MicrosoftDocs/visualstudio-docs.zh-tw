---
title: 記憶體和分頁效能規則 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d10d423c544a1117a56a954bacfa00f0ce439b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808637"
---
# <a name="memory-and-paging-performance-rules"></a>記憶體和分頁效能規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

記憶體和分頁分類中的效能規則，會在執行的分析中找出可能影響應用程式效能和回應性的分頁活動。  
  
|||  
|-|-|  
|[DA0014：極高比率的使用中記憶體分頁到磁碟](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|在執行分析的過程中，磁碟使用中的記憶體有極高的比率會發生來回分頁。 此程度的分頁比率通常會影響應用程式效能和回應性。 請考慮修改演算法減少記憶體配置。 您也必須考慮應用程式的記憶體需求。 請在有較多記憶體的電腦上再次嘗試執行分析。 當分頁活動量超過規則 D0017 的上限臨界值時，就會引發此規則。|  
|[DA0017：高比率的使用中記憶體分頁到磁碟](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|在執行分析的過程中，磁碟使用中的記憶體有相當高的比率會發生來回分頁。 此程度的分頁比率通常會影響應用程式效能和回應性。 請考慮修改演算法減少記憶體配置。 您也必須考慮應用程式的記憶體需求。 請在有較多記憶體的電腦上再次嘗試執行分析。|



