---
title: IDebugSymbolProvider::GetTypeByName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetTypeByName method
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b95117cd37f9ca6c2bfe3d2276bb03994f7a07b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924732"
---
# <a name="idebugsymbolprovidergettypebyname"></a>IDebugSymbolProvider::GetTypeByName
這個方法會對應至符號類型的符號名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeByName(   
   LPCOLESTR     pszClassName,  
   NAME_MATCH    nameMatch,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeByName(  
   string          pszClassName,   
   NAME_MATCH      nameMatch,   
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszClassName`  
 [in]符號名稱。  
  
 `nameMatch`  
 [in]選取類型的相符項目，例如，區分大小寫。 值，以從[NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)列舉型別。  
  
 `ppField`  
 [out]傳回與符號類型[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法是泛型版本[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)