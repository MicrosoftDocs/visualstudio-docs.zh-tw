---
title: "IActiveScriptSiteDebug 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug 介面
實作智慧主機`IActiveScriptSiteDebug`執行文件管理，並參與偵錯介面。 `IActiveScriptSite`物件通常會提供的實作`IActiveScriptSiteDebug`介面。 如果這麼做，呼叫`IActiveScriptSite::QueryInterface`方法，以取得`IActiveScriptSiteDebug`介面。  
  
 除了繼承自`IUnknown`、`IActiveScriptSiteDebug`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|語言引擎用於委派`IDebugCodeContext::GetSourceContext`。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|傳回與此指令碼的站台相關聯的偵錯應用程式物件。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|取得應該在哪種指令碼加入文件的應用程式節點。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|可讓智慧主機來判斷如何處理執行階段錯誤。|