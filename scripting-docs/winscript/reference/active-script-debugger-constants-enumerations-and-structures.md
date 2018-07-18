---
title: 使用中指令碼偵錯工具的常數、 列舉和結構 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bd41fe91fdf030b957d800248343198f2617018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642068"
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>動態指令碼偵錯工具的常數、列舉和結構
Active Debugging 介面會使用下列常數、列舉和結構。  
  
## <a name="constants-enumerations-and-structures"></a>常數、列舉和結構  
  
|常數|說明|  
|---------------|-----------------|  
|[APPBREAKFLAGS 常數](../../winscript/reference/appbreakflags-enumeration.md)|指出應用程式和執行緒的目前偵錯狀態。|  
|[DEBUG_TEXT 常數](../../winscript/reference/debug-text-constants.md)|選項旗標用於[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)。|  
|[TEXT_DOC_ATTR 常數](../../winscript/reference/text-doc-attr-constants.md)|描述文件的屬性。|  
  
|列舉|說明|  
|------------------|-----------------|  
|[APPBREAKFLAGS 常數](../../winscript/reference/appbreakflags-enumeration.md)|指出應用程式和執行緒的目前偵錯狀態。|  
|[APPLICATION_NODE_EVENT_FILTER 列舉](../../winscript/reference/application-node-event-filter-enumeration.md)|指出要使用篩選條件排除的節點。|  
|[BREAKPOINT_STATE 列舉](../../winscript/reference/breakpoint-state-enumeration.md)|指出中斷點的狀態。|  
|[BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)|指出造成中斷的原因。|  
|[BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)|描述如何從中斷點繼續執行。|  
|[DOCUMENTNAMETYPE 列舉](../../winscript/reference/documentnametype-enumeration.md)|描述要為文件取得的類型。|  
|[ERRORRESUMEACTION 列舉](../../winscript/reference/errorresumeaction-enumeration.md)|描述如何從執行階段錯誤繼續執行。|  
|[JS_PROPERTY_ATTRIBUTES 列舉](../../winscript/reference/js-property-attributes-enumeration.md)|指出屬性 (Property) 的屬性 (Attribute)。|  
|[JS_PROPERTY_MEMBERS 列舉](../../winscript/reference/js-property-members-enumeration.md)|旗標，用於指定在物件成員的要求中傳回的資訊類型。|  
|[JsDebugReadMemoryFlags 列舉](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|旗標，用於指定讀取記憶體時的行為。|  
|[SCRIPT_DEBUGGER_OPTIONS 列舉](../../winscript/reference/script-debugger-options-enumeration.md)|表示套用至附加偵錯工具的一組選項或功能。|  
|[SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列舉](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|指出擲回的例外狀況類型。|  
|[SOURCE_TEXT_ATTR 常數](../../winscript/reference/source-text-attr-enumeration.md)|描述原始程式文字的單一字元的屬性。|  
  
|結構|說明|  
|----------------|-----------------|  
|[DebugStackFrameDescriptor 結構](../../winscript/reference/debugstackframedescriptor-structure.md)|會列舉堆疊框架並合併相同執行緒上數個列舉值的輸出。|  
|[JS_NATIVE_FRAME 結構](../../winscript/reference/js-native-frame-structure.md)|代表堆疊框架。|  
|[JsDebugPropertyInfo 結構](../../winscript/reference/jsdebugpropertyinfo-structure.md)|指出有關屬性的資訊。|  
|[TEXT_DOCUMENT_ARRAY 結構](../../winscript/reference/text-document-array-structure.md)|提供一組文件。|