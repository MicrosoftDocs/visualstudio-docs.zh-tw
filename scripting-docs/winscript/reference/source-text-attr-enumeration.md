---
title: "SOURCE_TEXT_ATTR 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR 列舉
描述原始程式文字的單一字元的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>成員  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|字元是語言關鍵字，例如，VBScript 關鍵字的一部分`While`。|  
|SOURCETEXT_ATTR_COMMENT|0x0002|字元是註解區塊的一部分。|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|字元不是語言編譯的原始程式文字的一部分。 例如，HTML 周圍的指令碼區塊。|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|字元是語言運算子的一部分。 例如:，算術運算子 **+** 。|  
|SOURCETEXT_ATTR_NUMBER|0x0010|字元是語言數值常數的一部分。  例如，常數 3.14159。|  
|SOURCETEXT_ATTR_STRING|0x0020|字元是語言的字串常數的一部分。 例如，字串"Hello World"。|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|字元表示函式區塊的開始|  
  
## <a name="remarks"></a>備註  
 一般而言， `IDebugDocumentHost::GetScriptTextAttributes`， `IActiveScriptDebug::GetScriptletTextAttributes`，和`IActiveScriptDebug::GetScriptTextAttributes`方法會傳回一個文字屬性，每個字元，除非：  
  
-   設定 GETATTRTYPE_DEPSCAN 旗標，方法可能會在此情況下傳回 SOURCETEXT_ATTR_IDENTIFIER 和 SOURCETEXT_ATTR_MEMBERLOOKUP 旗標，  
  
-   設定 GETATTRFLAG_THIS 旗標，方法可能會在此情況下傳回 SOURCETEXT_ATTR_THIS 旗標  
  
-   已設定 GETATTRFLAG_HUMANTEXT 旗標，方法可能會在此情況下傳回 SOURCETEXT_ATTR_HUMANTEXT 旗標。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)