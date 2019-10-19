---
title: SOURCE_TEXT_ATTR 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572999"
---
# <a name="source_text_attr-enumeration"></a>SOURCE_TEXT_ATTR 列舉
描述原始程式文字的單一字元的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Members  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|字元是 language 關鍵字的一部分，例如，VBScript 關鍵字 `While`。|  
|SOURCETEXT_ATTR_COMMENT|0x0002|字元是批註區塊的一部分。|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|字元不是已編譯語言來源文字的一部分。 例如，腳本區塊周圍的 HTML。|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|字元是語言運算子的一部分。 例如：，算術運算子 **+** 。|  
|SOURCETEXT_ATTR_NUMBER|0x0010|字元是語言數值常數的一部分。  例如，常數3.14159。|  
|SOURCETEXT_ATTR_STRING|0x0020|字元是語言字串常數的一部分。 例如，字串 "Hello World"。|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|字元表示函式區塊的開頭|  
  
## <a name="remarks"></a>備註  
 一般來說，`IDebugDocumentHost::GetScriptTextAttributes`、`IActiveScriptDebug::GetScriptletTextAttributes` 和 `IActiveScriptDebug::GetScriptTextAttributes` 方法會針對每個字元傳回一個 text 屬性，除非：  
  
- 已設定 GETATTRTYPE_DEPSCAN 旗標，在此情況下，此方法可能會傳回 SOURCETEXT_ATTR_IDENTIFIER 和 SOURCETEXT_ATTR_MEMBERLOOKUP 旗標。  
  
- 已設定 GETATTRFLAG_THIS 旗標，在此情況下，此方法可能會傳回 SOURCETEXT_ATTR_THIS 旗標。  
  
- 已設定 GETATTRFLAG_HUMANTEXT 旗標，在此情況下，方法可能會傳回 SOURCETEXT_ATTR_HUMANTEXT 旗標。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)