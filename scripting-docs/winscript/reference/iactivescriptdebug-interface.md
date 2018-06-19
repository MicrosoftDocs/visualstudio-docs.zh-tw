---
title: IActiveScriptDebug 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645818"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug 介面
實作該支援偵錯指令碼引擎。 一般而言，該物件會實作`IActiveScriptDebug`介面也會實作`IActiveScript`介面。 如果這種情況，呼叫`IActiveScript::QueryInterface`方法，以取得`IActiveScriptDebug`介面。  
  
 `IActiveScriptDebug`介面提供的方式：  
  
-   智慧主機接管文件管理。  
  
-   同步處理的多個指令碼引擎偵錯的偵錯處理序管理員。  
  
 除了繼承自`IUnknown`、`IActiveScriptDebug`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|傳回指令碼文字的任意區塊的文字屬性。|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|傳回任意程式碼片段的文字屬性。|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|委派給`IDebugDocumentContext::EnumCodeContexts`。|