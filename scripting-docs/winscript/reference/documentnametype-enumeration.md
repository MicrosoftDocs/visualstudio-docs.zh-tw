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
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955208"
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|取得出現在樹狀目錄中的應用程式名稱。|  
|DOCUMENTNAMETYPE_TITLE|檢視器的標題列上所顯示的樣子，請取得的名稱。|  
|DOCUMENTNAMETYPE_FILE_TAIL|取得不具路徑的檔案名稱。|  
|DOCUMENTNAMETYPE_URL|取得文件的 URL。|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|取得加上列舉型別識別的標題。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)