---
title: BP_LOCATION_CODE_STRING |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ef3e7c80dff276dd3bb251782d8dc07b3f5ac00
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795306"
---
# <a name="bplocationcodestring"></a>BP_LOCATION_CODE_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

用於設定使用者可以輸入從整合式的開發環境 (IDE) 的字串為基礎的程式碼中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## <a name="members"></a>成員  
 `bstrContext`  
 程式碼內的中斷點，通常是方法或函式的名稱為 呼叫堆疊上看到的內容。  
  
 `bstrCodeExpr`  
 字串，使用者輸入來描述程式碼中斷點。  
  
## <a name="remarks"></a>備註  
 此結構是隸屬[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構的聯集的一部分。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)

