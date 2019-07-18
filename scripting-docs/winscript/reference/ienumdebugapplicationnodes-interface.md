---
title: IEnumDebugApplicationNodes Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugApplicationNodes interface
ms.assetid: 4fd38b44-3f9a-4d23-9a8f-7dc98f72725f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d23f8a8eaa8e10c503d7ec73f4cd5d4f6ea24404
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951732"
---
# <a name="ienumdebugapplicationnodes-interface"></a>IEnumDebugApplicationNodes 介面
列舉與應用程式建立關聯之節點的子節點。  
  
 除了繼承自方法`IUnknown`，則`IEnumDebugApplicationNodes`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumDebugApplicationNodes::Next](../../winscript/reference/ienumdebugapplicationnodes-next.md)|擷取指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugApplicationNodes::Skip](../../winscript/reference/ienumdebugapplicationnodes-skip.md)|略過指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugApplicationNodes::Reset](../../winscript/reference/ienumdebugapplicationnodes-reset.md)|將列舉型別序列重設到開頭。|  
|[IEnumDebugApplicationNodes::Clone](../../winscript/reference/ienumdebugapplicationnodes-clone.md)|建立列舉值，包含目前的列舉值相同的狀態。|