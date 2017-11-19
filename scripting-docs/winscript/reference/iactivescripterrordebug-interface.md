---
title: "IActiveScriptErrorDebug 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ff2dda33c1e406f87a157173c41015acf96e62a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug 介面
提供編譯時間錯誤和執行階段例外狀況的文件內容資訊。 `IActiveScriptError::QueryInterface`方法可支援`IActiveScriptErrorDebug`介面。  
  
 除了繼承自`IActiveScriptError`、`IActiveScriptErrorDebug`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|此錯誤提供的文件內容。|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|提供適用於執行階段錯誤的作用中堆疊框架。|