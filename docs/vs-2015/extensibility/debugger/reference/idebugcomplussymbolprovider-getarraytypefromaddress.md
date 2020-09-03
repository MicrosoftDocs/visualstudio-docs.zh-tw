---
title: IDebugComPlusSymbolProvider：： GetArrayTypeFromAddress |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetArrayTypeFromAddress
- IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
ms.assetid: cc0c53f1-8c0f-49fa-8dbe-bc155e9ce0ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a0b211b1bf857b65a9c9071855c24dc7b4f30e21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194791"
---
# <a name="idebugcomplussymbolprovidergetarraytypefromaddress"></a>IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得指定之陣列的調試位址的型別資訊。  
  
## <a name="syntax"></a>語法  
  
```  
[C++]  
HRESULT GetArrayTypeFromAddress(  
   IDebugAddress* pAddress,  
   BYTE*          pSig,  
   DWORD          dwSigLength,  
   IDebugField**  ppField  
);  
```  
  
```  
[C#]  
int GetArrayTypeFromAddress(  
   IDebugAddress   pAddress,  
   int[]           pSig,  
   uint            dwSigLength,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 在 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面所代表的偵錯工具位址。  
  
 `pSig`  
 在要檢查的陣列。  
  
 `dwSigLength`  
 在陣列的長度（以位元組為單位） `pSig` 。  
  
 `ppField`  
 擴展傳回 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 介面所代表的陣列類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何針對公開[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的**CDebugSymbolProvider**物件，執行這個方法。  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetArrayTypeFromAddress(  
    IDebugAddress *pAddress,  
    BYTE *pSig,  
    DWORD dwSigLength,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
    CDEBUG_ADDRESS da;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    IfFailGo( pAddress->GetAddress(&da) );  
  
    if ( S_OK == hr )  
    {  
        IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );  
  
        IfFailGo( this->CreateType((const COR_SIGNATURE*)(pSig), dwSigLength, da.GetModule(), mdMethodDefNil, pGenScope, ppField) );  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress, hr );  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
