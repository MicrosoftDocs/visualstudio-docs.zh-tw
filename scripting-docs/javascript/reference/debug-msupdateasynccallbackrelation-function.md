---
title: Debug.msUpdateAsyncCallbackRelation 函式 |Microsoft 文件
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c47ed7f6313646dddf86dd766d7f1027b2d38ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636218"
---
# <a name="debugmsupdateasynccallbackrelation-function"></a>Debug.msUpdateAsyncCallbackRelation 函式
更新同步工作項目和關聯的非同步作業之間的關聯性狀態。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### <a name="parameters"></a>參數  
 `relatedAsyncOperationId`  
 必要項。 與非同步作業相關聯的 ID。  
  
 `relationType`  
 選擇項。 指定關聯性狀態的值。  
  
## <a name="remarks"></a>備註  
 同步工作項目通常是非同步作業的回呼函式。 當非同步作業中止、當使用聯結作業，或在其他案例中，都可以呼叫這個函式。  
  
 `relationType` 的可能值包括︰  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 如需詳細資訊，請參閱[偵錯常數](../../javascript/reference/debug-constants.md)。  
  
> [!NOTE]
>  部分偵錯工具不會顯示這個函式傳送至偵錯工具的資訊。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]