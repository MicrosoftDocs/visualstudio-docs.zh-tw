---
title: IDebugExpressionEvaluator2：:P reloadModules |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d6d7236f19032fa0767a050ac84afe4b4e1585f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540234"
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

預先載入指定的符號提供者所指定的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT PreloadModules (  
   IDebugSymbolProvider* pSym  
);  
```  
  
```csharp  
int PreloadModules (  
   IDebugSymbolProvider pSym  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSym`  
 在將預先載入模組的符號提供者。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當您進行主機進程附加時，會使用這個選擇性方法。 它讓 EE 有機會在連接過程中「準備」。  
  
## <a name="example"></a>範例  
 下列範例示範如何針對公開[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)介面的**ExpressionEvaluatorPackage**物件，執行這個方法。  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules  
(  
    IDebugSymbolProvider *pSym  
)  
{  
    HRESULT hr = NOERROR;  
    RuntimeMemberDescriptor  * prtMemberDesc;  
    RuntimeClassDescriptor *prtClassDesc;  
    CComPtr<IDebugClassField> pClassField;  
    IfFalseGo(pSym,E_INVALIDARG);  
  
    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
    pClassField = NULL;  
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
Error:  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
