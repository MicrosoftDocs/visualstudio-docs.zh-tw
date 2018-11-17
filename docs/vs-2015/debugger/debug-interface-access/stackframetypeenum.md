---
title: StackFrameTypeEnum |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de80fd054459556e273427b666175751ced203fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740375"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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



