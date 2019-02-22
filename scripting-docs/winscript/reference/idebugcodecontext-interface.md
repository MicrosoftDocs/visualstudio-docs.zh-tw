---
title: IDebugCodeContext 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext interface
ms.assetid: ae1264d5-1ac2-4b04-9fa5-958212543975
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0840bf0a77a671bd2a37c49db48d1eb1cd5fa222
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349162"
---
# <a name="idebugcodecontext-interface"></a>IDebugCodeContext 介面
抽象型別，表示可執行程式碼中的位置。  
  
 除了繼承自方法`IUnknown`，則`IDebugCodeContext`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugCodeContext::GetDocumentContext](../../winscript/reference/idebugcodecontext-getdocumentcontext.md)|傳回與此程式碼內容相關聯的文件內容。|  
|[IDebugCodeContext::SetBreakPoint](../../winscript/reference/idebugcodecontext-setbreakpoint.md)|設定或清除在本文中的程式碼中斷點。|