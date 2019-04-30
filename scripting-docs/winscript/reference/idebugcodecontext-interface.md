---
title: IDebugCodeContext 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f3d3d1834d176a323778ae9b7d215951d1a26bb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821740"
---
# <a name="idebugcodecontext-interface"></a>IDebugCodeContext 介面
抽象型別，表示可執行程式碼中的位置。  
  
 除了繼承自方法`IUnknown`，則`IDebugCodeContext`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugCodeContext::GetDocumentContext](../../winscript/reference/idebugcodecontext-getdocumentcontext.md)|傳回與此程式碼內容相關聯的文件內容。|  
|[IDebugCodeContext::SetBreakPoint](../../winscript/reference/idebugcodecontext-setbreakpoint.md)|設定或清除在本文中的程式碼中斷點。|