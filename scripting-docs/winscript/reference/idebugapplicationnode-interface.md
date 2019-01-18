---
title: IDebugApplicationNode Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7bd38a0fbbdd596f6a1f6bb040190dddca78bf9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348993"
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode 介面
`IDebugApplicationNode`介面會擴充功能的`IDebugDocumentProvider`介面藉由提供專案樹狀結構內的內容。  
  
 除了繼承自方法`IDebugDocumentProvider`，則`IDebugApplicationNode`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|列舉此應用程式 節點的子節點。|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|傳回此應用程式 節點的父節點。|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|設定此應用程式 節點的文件提供者。|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|造成此應用程式以發行所有參考，然後輸入 非作用中狀態。|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|此應用程式將節點加入至指定的專案樹狀結構。|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|從專案樹狀結構中移除此應用程式 節點。|