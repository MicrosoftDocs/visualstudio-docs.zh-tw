---
title: "IDebugApplicationNode100 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 介面
`IDebugApplicationNode100`介面延伸功能的[IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)。 您可以取得此介面的執行個體的實作上呼叫 QueryInterface [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)。  
  
> [!IMPORTANT]
>  這個介面會實作由 PDM v10.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugApplicationNode100` 介面公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|取得所指定的篩選條件會隱藏文字文件。|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|判斷指定的文件是否屬於這個節點的子節點的其中一個。|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|在特定設定的篩選條件[IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md)實作。 它可讓指令碼偵錯工具若要篩選出編譯器產生的子應用程式節點，使 PDM 將不會再傳送事件時建立或移除節點。 根據預設，會傳送所有節點。|