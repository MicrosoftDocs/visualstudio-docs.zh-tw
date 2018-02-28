---
title: "IEnumDebugCodeContexts 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IEnumDebugCodeContexts interface
ms.assetid: 47f17dc9-14bc-43c8-b874-00b5802076eb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45e28f91b6637142fabfdb3680479c474a75f03d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugcodecontexts-interface"></a>IEnumDebugCodeContexts 介面
列舉對應至文件內容的程式碼內容。  
  
 除了繼承自`IUnknown`、`IEnumDebugCodeContexts`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IEnumDebugCodeContexts::Next](../../winscript/reference/ienumdebugcodecontexts-next.md)|擷取指定的列舉順序中的區段數目。|  
|[IEnumDebugCodeContexts::Skip](../../winscript/reference/ienumdebugcodecontexts-skip.md)|略過指定的數目的列舉順序中的區段。|  
|[IEnumDebugCodeContexts::Reset](../../winscript/reference/ienumdebugcodecontexts-reset.md)|列舉序列重設為開頭。|  
|[IEnumDebugCodeContexts::Clone](../../winscript/reference/ienumdebugcodecontexts-clone.md)|建立列舉值，包含目前的列舉值的狀態相同。|