---
title: StackFrameTypeEnum |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 081be0d7b9369462bae703b571629897bd5df94c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487087"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[StackFrameTypeEnum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/stackframetypeenum)。  
  
指定的堆疊框架的類型。  
  
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
 框架指標省略;畫面格的資料可用的資訊。  
  
 `FrameTypeUnknown`  
 沒有任何偵錯資訊的框架。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳回呼叫[idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



