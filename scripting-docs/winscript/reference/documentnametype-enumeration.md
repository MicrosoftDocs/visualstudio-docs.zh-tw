---
title: "DOCUMENTNAMETYPE 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE 列舉
描述要為文件取得的類型。  
  
## <a name="syntax"></a>語法  
  
```  
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
|DOCUMENTNAMETYPE_APPNODE|出現在應用程式的樹狀目錄中取得的名稱。|  
|DOCUMENTNAMETYPE_TITLE|取得名稱，因為它會出現在檢視器的標題列。|  
|DOCUMENTNAMETYPE_FILE_TAIL|取得檔案名稱，如果沒有指定路徑。|  
|DOCUMENTNAMETYPE_URL|取得文件的 URL。|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|取得附加列舉識別的標題。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)