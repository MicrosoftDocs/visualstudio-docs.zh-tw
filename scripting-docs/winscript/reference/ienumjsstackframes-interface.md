---
title: IEnumJsStackFrames Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e8302737fb4abf96c55d3ae70424cc03579b270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963321"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames 介面
藉由將偵錯工具提供堆疊回溯適用於 JavaScript 的 jscript9diag.dll。  
  
## <a name="syntax"></a>語法  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next 方法](../../winscript/reference/ienumjsstackframes-next-method.md)|取得指定的框架數。|  
|[IEnumJsStackFrames::Reset 方法](../../winscript/reference/ienumjsstackframes-reset-method.md)|將堆疊框架重設之前的第一個元素的位置。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)