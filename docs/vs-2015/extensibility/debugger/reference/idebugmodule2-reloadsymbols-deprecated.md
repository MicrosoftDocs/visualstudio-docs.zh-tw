---
title: IDebugModule2::ReloadSymbols_Deprecated |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ce816e20e59d407f9b3cd84e3dffa703d84a324
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189550"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

已過時。 請勿使用。 重新載入此模組的符號。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszUrlToSymbols`  
 [in]符號存放區的路徑。  
  
 `pbstrDebugMessage`  
 [out]傳回參考用訊息，例如狀態或錯誤訊息，顯示右邊的 [模組] 視窗中的模組名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 偵錯引擎應該一律傳回`E_FAIL`。  
  
## <a name="remarks"></a>備註  
 不再支援這個方法。 實作[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)方法改為。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
