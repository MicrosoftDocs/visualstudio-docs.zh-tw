---
title: TEXT_DOCUMENT_ARRAY 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d188729b68f8086da62d40ca28fc29945c8be7f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152232"
---
# <a name="textdocumentarray-structure"></a>TEXT_DOCUMENT_ARRAY 結構
陣列[IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)物件。 成員會以 CoTaskMemAlloc 來配置。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>成員  
 `dwCount`  
 文件數目。  
  
 `Members`  
 文件集。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)