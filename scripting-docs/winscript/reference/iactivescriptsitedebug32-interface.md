---
title: IActiveScriptSiteDebug32 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835260"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 介面
智慧型主機會實作為 `IActiveScriptSiteDebug32` 執行檔管理和參與調試的介面。 `IActiveScriptSite`物件通常會提供介面的執行 `IActiveScriptSiteDebug32` 。 如果這樣做，請呼叫 `IActiveScriptSite::QueryInterface` 方法來取得 `IActiveScriptSiteDebug32` 介面。  
  
 除了繼承自的方法之外 `IUnknown` ，介面也會 `IActiveScriptSiteDebug32` 公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|傳回與這個腳本網站相關聯的 debug 應用程式物件。|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|供語言引擎用來委派 `IDebugCodeContext::GetSourceContext` 。|