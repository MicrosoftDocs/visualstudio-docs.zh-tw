---
title: IActiveScriptSiteDebug 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cd8043648586ed3c614cbb137e51d992d7ae29b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145774"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug 介面
實作智慧主機`IActiveScriptSiteDebug`介面來執行文件管理，以及參與偵錯。 `IActiveScriptSite`物件通常會提供實作`IActiveScriptSiteDebug`介面。 如果這麼做，呼叫`IActiveScriptSite::QueryInterface`方法，以取得`IActiveScriptSiteDebug`介面。  
  
 除了繼承自方法`IUnknown`，則`IActiveScriptSiteDebug`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|語言引擎用來委派`IDebugCodeContext::GetSourceContext`。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|傳回與這個指令碼網站相關聯的偵錯應用程式物件。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|取得應該在哪種指令碼加入文件的應用程式節點。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|可讓智慧主機，以判斷如何處理執行階段錯誤。|