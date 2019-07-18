---
title: IDebugFunctionObject2::CreateObject |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b60801f5288e88795ab75145b9c6120d4308d1c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202988"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立會使用指定評估旗標設定和逾時值的建構函式的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pConstructor`  
 [in][IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)物件，表示要建立之物件的建構函式。  
  
 `dwArgs`  
 [in]中的參數數目`pArg`陣列。 表示傳遞至建構函式的參數數目。  
  
 `pArgs`  
 [in]陣列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，表示的參數傳遞至建構函式。  
  
 `dwEvalFlags`  
 [in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉，指定要如何進行評估。  
  
 `dwTimeout`  
 [in]最大時間 （毫秒），這個方法返回之前等候。 使用**無限**無限期等候。  
  
 `ppObject`  
 [out]傳回**IDebugObject**代表新建立的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法來建立物件，表示類別或其他需要的建構函式，為參數的複雜類型的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
