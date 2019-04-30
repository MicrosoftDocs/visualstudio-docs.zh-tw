---
title: TEXT_DOC_ATTR 的常數 |Microsoft Docs
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
ms.openlocfilehash: d22b178d85d304f19e52727ef2c67d77f16da1b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840079"
---
# <a name="textdocattr-constants"></a>TEXT_DOC_ATTR 的常數
描述文件的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>常數  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|文件是唯讀的。|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|文件是此文件樹狀結構的主要檔案。|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|文件是背景工作角色。|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|文件是指令碼檔案。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)