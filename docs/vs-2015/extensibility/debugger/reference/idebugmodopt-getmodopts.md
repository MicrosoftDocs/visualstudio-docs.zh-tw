---
title: IDebugModOpt::GetModOpts |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8abd62f63f3b2aa6b4b77dd94bd9b3db208dd22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848367"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取一份選擇性修飾詞。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]要傳回的項目數目。  
  
 `rgelt`  
 [out]傳回陣列，其中包含的選項。  
  
 `pceltFetched`  
 [in、 out]在傳回的項目數`rgelt`陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)

