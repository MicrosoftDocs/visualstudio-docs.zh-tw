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
ms.openlocfilehash: cf4933cc5778dd4af21e1b12d64fc59d371ad097
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238214"
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO 列舉
表示正在追蹤的腳本事件。 用於 [IActiveScriptSiteTraceInfo：： SendScriptTraceInfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)中。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|值|指令碼事件|  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|腳本的開頭。|  
|SCRIPTTRACEINFO_SCRIPTEND|腳本的結尾。|  
|SCRIPTTRACEINFO_COMCALLSTART|COM 呼叫的開頭。|  
|SCRIPTTRACEINFO_COMCALLEND|COM 呼叫的結尾。|  
|SCRIPTTRACEINFO_CREATEOBJSTART|建立物件的起點。|  
|SCRIPTTRACEINFO_CREATEOBJEND|建立物件的結尾。|  
|SCRIPTTRACEINFO_GETOBJSTART|GetObject 呼叫的開頭。|  
|SCRIPTTRACEINFO_GETOBJEND|GetObject 呼叫的結尾。|