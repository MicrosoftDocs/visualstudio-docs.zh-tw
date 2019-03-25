---
title: SCRIPTTRACEINFO 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ed2c6566db8209280be7f102a55c7de8cf85c44
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155806"
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO 列舉
表示所追蹤的指令碼事件。 用於[iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|指令碼開頭。|  
|SCRIPTTRACEINFO_SCRIPTEND|指令碼結尾。|  
|SCRIPTTRACEINFO_COMCALLSTART|COM 呼叫的開始。|  
|SCRIPTTRACEINFO_COMCALLEND|COM 呼叫端。|  
|SCRIPTTRACEINFO_CREATEOBJSTART|建立的開始物件。|  
|SCRIPTTRACEINFO_CREATEOBJEND|建立物件結尾。|  
|SCRIPTTRACEINFO_GETOBJSTART|GetObject 呼叫的開始。|  
|SCRIPTTRACEINFO_GETOBJEND|GetObject 呼叫端。|