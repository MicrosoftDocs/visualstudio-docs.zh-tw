---
title: "StackFrameTypeEnum |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4dcb46fc2fb3936e0cee91426b4787945bd14f59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
指定堆疊框架類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>項目  
 `FrameTypeFPO`  
 框架指標省略;FPO 資訊可用。  
  
 `FrameTypeTrap`  
 核心設陷框架。  
  
 `FrameTypeTSS`  
 核心設陷框架。  
  
 `FrameTypeStandard`  
 標準的 EBP 堆疊框架。  
  
 `FrameTypeFrameData`  
 框架指標省略;框架資料可用的資訊。  
  
 `FrameTypeUnknown`  
 沒有任何偵錯資訊的框架。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳回透過呼叫[idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)