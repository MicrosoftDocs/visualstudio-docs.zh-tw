---
title: IEnumJsStackFrames 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12583f73c9f3977371ebd193716f2513fc0befc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727318"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames 介面
藉由偵錯工具提供堆疊回溯 jscript9diag.dll javascript。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next 方法](../../winscript/reference/ienumjsstackframes-next-method.md)|取得指定的框架數。|  
|[IEnumJsStackFrames::Reset 方法](../../winscript/reference/ienumjsstackframes-reset-method.md)|將堆疊框架重設前的第一個元素的位置。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)