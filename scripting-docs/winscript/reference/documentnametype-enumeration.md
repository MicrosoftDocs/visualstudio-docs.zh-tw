---
title: DOCUMENTNAMETYPE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094766"
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