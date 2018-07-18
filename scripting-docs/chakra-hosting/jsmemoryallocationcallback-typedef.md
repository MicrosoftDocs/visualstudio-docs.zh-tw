---
title: JsMemoryAllocationCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568728"
---
# <a name="jsmemoryallocationcallback-typedef"></a>JsMemoryAllocationCallback Typedef
使用者針對記憶體配置事件實作的回呼常式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 callbackState  
 傳遞給 JsSetRuntimeMemoryAllocationCallback 的狀態。  
  
 allocationEvent  
 類型配置事件的類型。  
  
 allocationSize  
 配置的大小。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 若為 JsMemoryAllocate 事件，傳回 true 可讓執行階段繼續配置； 傳回 false 表示拒絕配置要求。 已忽略其他配置事件的傳回值。  
  
## <a name="remarks"></a>備註  
 使用 JsSetRuntimeMemoryAllocationCallback 註冊這個回呼。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)