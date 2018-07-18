---
title: SCRIPTTRACEINFO 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1902b290a8024679cef12d503e94de4923defb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733988"
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO 列舉
表示所追蹤的指令碼事件。 用於[iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|指令碼的起點。|  
|SCRIPTTRACEINFO_SCRIPTEND|指令碼結尾。|  
|SCRIPTTRACEINFO_COMCALLSTART|COM 呼叫的開始。|  
|SCRIPTTRACEINFO_COMCALLEND|COM 呼叫的結尾。|  
|SCRIPTTRACEINFO_CREATEOBJSTART|建立物件開始。|  
|SCRIPTTRACEINFO_CREATEOBJEND|建立物件的結尾。|  
|SCRIPTTRACEINFO_GETOBJSTART|GetObject 呼叫的開始。|  
|SCRIPTTRACEINFO_GETOBJEND|GetObject 呼叫的結尾。|