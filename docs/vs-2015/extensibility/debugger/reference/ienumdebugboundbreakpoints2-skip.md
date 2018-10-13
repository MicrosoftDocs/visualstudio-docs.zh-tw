---
title: IEnumDebugBoundBreakpoints2::Skip |Microsoft Docs
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
- IEnumDebugBoundBreakpoints2::Skip
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Skip
ms.assetid: 95659709-6d7c-44ca-b598-629eb688429f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65540a995b4ba5dee64486f77e236bba53d2dfec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298593"
---
# <a name="ienumdebugboundbreakpoints2skip"></a>IEnumDebugBoundBreakpoints2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

略過指定的元素數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]略過的項目數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 會傳回`S_FALSE`如果`celt`大於其餘項目數目，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果`celt`指定的值大於其餘的項目，列舉型別設定為結束和`S_FALSE`會傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)

