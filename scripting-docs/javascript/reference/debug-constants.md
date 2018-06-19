---
title: 偵錯常數 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636148"
---
# <a name="debug-constants"></a>偵錯常數
偵錯常數會傳回屬於 `Debug` 物件屬性的常數值。  
  
## <a name="debug-object-constants"></a>Debug 物件常數  
 下表列出是屬性的常數值[Debug 物件](../../javascript/reference/debug-object-javascript.md)。  
  
|常數|描述|值|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|同步工作項目指派要由非同步作業執行的回呼或接續。|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|同步工作項目滿足聯結非同步作業的一部分。|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|同步工作項目滿足選擇非同步作業。|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|同步工作項目已取消。|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|同步工作項目在非同步作業中造成錯誤。|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|非同步作業成功。|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|非同步作業已取消。|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|非同步作業已產生錯誤。|3|  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Debug.msTraceAsyncOperationCompleted 函式](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation 函式](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)