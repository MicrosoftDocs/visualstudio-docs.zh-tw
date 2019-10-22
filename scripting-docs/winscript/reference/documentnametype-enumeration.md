---
title: DOCUMENTNAMETYPE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575868"
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE 列舉
描述要為文件取得的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|取得在應用程式樹狀結構中顯示的名稱。|  
|DOCUMENTNAMETYPE_TITLE|取得顯示在檢視器標題列上的名稱。|  
|DOCUMENTNAMETYPE_FILE_TAIL|取得沒有路徑的檔案名。|  
|DOCUMENTNAMETYPE_URL|取得檔的 URL。|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|取得附加列舉的標題，以供識別之用。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)