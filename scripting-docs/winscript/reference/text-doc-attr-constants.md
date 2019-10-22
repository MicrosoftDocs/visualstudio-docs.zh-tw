---
title: TEXT_DOC_ATTR 常數 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3604c06b6cb36cc4ff7ef6c76348b5ece53bed61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572994"
---
# <a name="text_doc_attr-constants"></a>TEXT_DOC_ATTR 的常數
描述文件的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>常數  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|檔是唯讀的。|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|這份檔是此檔樹狀結構的主要檔案。|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|檔是背景工作角色。|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|這份檔是腳本檔案。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)