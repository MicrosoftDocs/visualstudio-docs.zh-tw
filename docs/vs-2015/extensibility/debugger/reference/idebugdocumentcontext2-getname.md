---
title: IDebugDocumentCoNtext2：： GetName |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1186b3b7d821be6861b992dfc6f2b744e8f722e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144942"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得包含此檔內容之檔的可顯示名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `gnType`  
 在 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 列舉中的值，這個值會指定要傳回的名稱類型。  
  
 `pbstrFileName`  
 擴展傳回檔案名。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法通常會將呼叫轉送至 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) 方法，除非檔內容是為了儲存檔案名稱本身 (，如範例顯示) 所示。  
  
## <a name="example"></a>範例  
 下列範例顯示如何針對 `CDebugContext` 公開 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 介面的簡單物件，執行這個方法。  
  
```cpp#  
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)    
{    
   HRESULT hr;    
  
   // Check for a valid file name argument.    
   if (pbstrFileName)    
   {    
      *pbstrFileName = NULL;    
  
      switch (gnType)    
      {    
         case GN_NAME:    
         case GN_FILENAME:    
         {    
            // Copy the member file name into the local file name.    
            *pbstrFileName = SysAllocString(m_sbstrFileName);    
            // Check for successful copy.    
            hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;    
            break;    
         }    
         default:    
         {    
            hr = E_FAIL;    
            break;    
         }    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
