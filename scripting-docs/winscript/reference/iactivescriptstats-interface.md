---
title: IActiveScriptStats 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptStats interface
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7a0e1e616fdee2dac58c8a5a1d24ed120b28bc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991967"
---
# <a name="iactivescriptstats-interface"></a>IActiveScriptStats 介面
可讓主應用程式能夠查詢執行的指令碼的統計資料。 主應用程式可以使用這項資訊來判斷是否指令碼已花費太多時間才能完成。  
  
 除了繼承自方法`IUnknown`，則`IActiveScriptStats`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|傳回其中一個標準的指令碼統計資料。|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|傳回自訂指令碼統計資料。|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|重設此指令碼的統計資料。|