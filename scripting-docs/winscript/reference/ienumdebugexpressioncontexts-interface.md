---
title: IEnumDebugExpressionContexts Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugExpressionContexts interface
ms.assetid: 1c11f9ff-c5a6-48b8-a287-0d782513ba55
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c257fe12f27bb5e6ffd5835986d0c7cac6193a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807370"
---
# <a name="ienumdebugexpressioncontexts-interface"></a>IEnumDebugExpressionContexts 介面
列舉 `IDebugExpressionContexts` 物件的集合。  
  
 除了繼承自方法`IUnknown`，則`IEnumDebugExpressionContexts`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumDebugExpressionContexts::Next](../../winscript/reference/ienumdebugexpressioncontexts-next.md)|擷取指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugExpressionContexts::Skip](../../winscript/reference/ienumdebugexpressioncontexts-skip.md)|略過指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugExpressionContexts::Reset](../../winscript/reference/ienumdebugexpressioncontexts-reset.md)|將列舉型別序列重設到開頭。|  
|[IEnumDebugExpressionContexts::Clone](../../winscript/reference/ienumdebugexpressioncontexts-clone.md)|建立列舉值，包含目前的列舉值相同的狀態。|