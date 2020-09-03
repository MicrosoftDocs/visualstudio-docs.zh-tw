---
title: IDebugProgram2：： EnumCodeCoNtexts |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 26bd68764b94aadccb796f33d127ba159e9c3727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202758"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

抓取原始程式檔中指定位置的程式碼內容清單。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```csharp  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDocPos`  
 在 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 物件，代表在 IDE 已知的原始程式檔中的抽象位置。  
  
 `ppEnum`  
 擴展傳回 [IEnumDebugCodeCoNtexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) 物件，其中包含程式碼內容的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法可讓會話 debug manager (SDM) 或 IDE，將原始程式檔位置對應到程式碼位置。 如果來源產生多個程式碼區塊，則會傳回一個以上的程式碼內容 (例如，c + + 範本) 。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
