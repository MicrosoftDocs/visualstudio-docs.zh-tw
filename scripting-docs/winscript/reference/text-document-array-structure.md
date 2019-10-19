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
ms.openlocfilehash: b52b382aa1e91e509672728a3c8f931bfeae27a9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572981"
---
# <a name="text_document_array-structure"></a>TEXT_DOCUMENT_ARRAY 結構
[IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)物件的陣列。 成員會使用 CoTaskMemAlloc 來配置。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Members  
 `dwCount`  
 檔的數目。  
  
 `Members`  
 一組檔。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)