---
title: IActiveScriptSiteDebug32 介面 |Microsoft 文件
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
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725118"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 介面
實作智慧主機`IActiveScriptSiteDebug32`執行文件管理，並參與偵錯介面。 `IActiveScriptSite`物件通常會提供的實作`IActiveScriptSiteDebug32`介面。 如果這麼做，呼叫`IActiveScriptSite::QueryInterface`方法，以取得`IActiveScriptSiteDebug32`介面。  
  
 除了繼承自`IUnknown`、`IActiveScriptSiteDebug32`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|傳回與此指令碼的站台相關聯的偵錯應用程式物件。|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|語言引擎用於委派`IDebugCodeContext::GetSourceContext`。|