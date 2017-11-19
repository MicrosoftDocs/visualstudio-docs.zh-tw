---
title: "IDebugApplicationNode 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode 介面
`IDebugApplicationNode`介面延伸功能的`IDebugDocumentProvider`介面提供在專案樹狀結構中的內容。  
  
 除了繼承自`IDebugDocumentProvider`、`IDebugApplicationNode`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|列舉此應用程式節點的子節點。|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|傳回這個應用程式節點的父節點。|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|設定此應用程式節點的文件提供者。|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|造成此應用程式以釋放所有參考，並輸入非作用中狀態。|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|此應用程式將節點加入至指定的專案樹狀結構。|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|從專案樹狀結構中移除此應用程式節點。|