---
title: IActiveScriptSiteDebug32 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345561"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 Interface
實作智慧主機`IActiveScriptSiteDebug32`介面來執行文件管理，以及參與偵錯。 `IActiveScriptSite`物件通常會提供實作`IActiveScriptSiteDebug32`介面。 如果這麼做，呼叫`IActiveScriptSite::QueryInterface`方法，以取得`IActiveScriptSiteDebug32`介面。  
  
 除了繼承自方法`IUnknown`，則`IActiveScriptSiteDebug32`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|傳回與這個指令碼網站相關聯的偵錯應用程式物件。|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|語言引擎用來委派`IDebugCodeContext::GetSourceContext`。|