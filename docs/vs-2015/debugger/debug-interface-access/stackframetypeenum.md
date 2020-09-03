---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179186"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定堆疊框架類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>元素  
 `FrameTypeFPO`  
 已省略框架指標;可用的 FPO 資訊。  
  
 `FrameTypeTrap`  
 核心陷阱框架。  
  
 `FrameTypeTSS`  
 核心陷阱框架。  
  
 `FrameTypeStandard`  
 標準 EBP 堆疊框架。  
  
 `FrameTypeFrameData`  
 已省略框架指標;可用的畫面格資料資訊。  
  
 `FrameTypeUnknown`  
 沒有任何偵錯工具資訊的框架。  
  
## <a name="remarks"></a>備註  
 呼叫 [IDiaStackFrame：： get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) 方法時，會傳回此列舉中的值。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst。h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
