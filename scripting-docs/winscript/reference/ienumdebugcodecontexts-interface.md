---
title: IEnumDebugCodeContexts 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugCodeContexts interface
ms.assetid: 47f17dc9-14bc-43c8-b874-00b5802076eb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e90e19a4bd12dfeeeef1b8f5498f729aa076adb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951469"
---
# <a name="ienumdebugcodecontexts-interface"></a>IEnumDebugCodeContexts 介面
列舉對應至文件內容的程式碼內容。  
  
 除了繼承自方法`IUnknown`，則`IEnumDebugCodeContexts`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumDebugCodeContexts::Next](../../winscript/reference/ienumdebugcodecontexts-next.md)|擷取指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugCodeContexts::Skip](../../winscript/reference/ienumdebugcodecontexts-skip.md)|略過指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugCodeContexts::Reset](../../winscript/reference/ienumdebugcodecontexts-reset.md)|將列舉型別序列重設到開頭。|  
|[IEnumDebugCodeContexts::Clone](../../winscript/reference/ienumdebugcodecontexts-clone.md)|建立列舉值，包含目前的列舉值相同的狀態。|