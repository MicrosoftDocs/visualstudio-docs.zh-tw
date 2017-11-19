---
title: "IDebugProperty3::GetStringChars |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::GetStringChars
helpviewer_keywords: IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2bf3dbc9e7c2696e51dfb86b8aa1c62b5f940655
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
擷取這個屬性與關聯的字串，並將它儲存在使用者提供的緩衝區。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `buflen`  
 [in]使用者提供的緩衝區可以保存最大字元數。  
  
 `rgString`  
 [out]傳回的字串。  
  
 [只有 c + +]`rgString`接收字串的 Unicode 字元的緩衝區的指標。 至少必須為這個緩衝區`buflen`字元 （而不是個位元組） 的大小。  
  
 `pceltFetched`  
 [out]其中會傳回實際儲存在緩衝區中的字元數。 (可以是`NULL`c + + 中。)  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在 c + +，必須小心以確保在緩衝區已至少`buflen`Unicode 字元。 請注意 Unicode 字元是 2 個位元組。  
  
> [!NOTE]
>  在 c + +，則傳回的字串不包含結束的 null 字元。 如果指定的話，`pceltFetched`會在字串中指定的字元數。  
  
## <a name="example"></a>範例  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>另請參閱  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)