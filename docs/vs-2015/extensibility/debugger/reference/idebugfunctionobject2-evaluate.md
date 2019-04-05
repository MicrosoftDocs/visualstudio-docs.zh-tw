---
title: IDebugFunctionObject2::Evaluate |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c25e62dbfc0778fb1bf07c9108c9111f3520d87f
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58946051"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

呼叫函式，並傳回產生的值當做物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppParams`  
 [in]陣列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)代表輸入的參數的物件。 每個參數建立這個介面中使用其中一種建立方法。  
  
 `dwParams`  
 [in]中的參數數目`ppParams`陣列。  
  
 `dwEvalFlags`  
 [in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉，指定要如何進行評估。  
  
 `dwTimeout`  
 [in]指定的時間上限，以毫秒為單位，從這個方法返回之前等候。 使用**無限**無限期等候。  
  
 `ppResult`  
 [out]傳回**IDebugObject**表示函式物件的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
