---
title: IDebugModule2::ReloadSymbols_Deprecated |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 09f2e81699683ec49155faceb375da3d636ed4c4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934037"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
已過時。 請勿使用。 重新載入此模組的符號。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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