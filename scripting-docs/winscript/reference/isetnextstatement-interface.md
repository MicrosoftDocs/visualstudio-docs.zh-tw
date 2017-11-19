---
title: "ISetNextStatement 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement 介面
實作這個介面是由解譯器以允許程序進行偵錯管理員來更新目前的陳述式。 它實作堆疊框架物件，並 PDM 取得 QueryInterface 透過此介面。  
  
 介面提供可用於設定執行點，用來決定要執行的下一個陳述式的方法。  
  
 除了繼承自`IUnknown`、`ISetNextStatement`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|決定是否可以設定執行點至指定的位置。|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|設定執行點至指定的位置。|