---
title: ISetNextStatement 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac2d6dd0da14be5a624cff0b55985770b8d70fdf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344053"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement 介面
此介面是由解譯器，以允許更新目前的陳述式的處理序偵錯管理員實作的。 它從堆疊框架物件，實作，PDM 取得 QueryInterface 透過此介面。  
  
 介面會提供可用於設定執行點，用來決定要執行下一個陳述式的方法。  
  
 除了繼承自方法`IUnknown`，則`ISetNextStatement`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|判斷是否可以設定執行點至指定的位置。|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|設定執行點至指定的位置。|