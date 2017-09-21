---
title: "IDebugDocumentContext2::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::EnumCodeContexts"
helpviewer_keywords: 
  - "IDebugDocumentContext2::EnumCodeContexts"
ms.assetid: 627af69c-5cce-4e1d-8233-5f4d8dbc62e5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugDocumentContext2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取一份與這個文件內容相關聯的所有程式碼內容。  
  
## 語法  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IEnumDebugCodeContexts2** ppEnumCodeCxts  
);  
```  
  
```c#  
int EnumCodeContexts(   
   out IEnumDebugCodeContexts2 ppEnumCodeCxts  
);  
```  
  
#### 參數  
 `ppEnumCodeCxts`  
 \[\] out傳回[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)物件，其中包含的程式碼內容的清單。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 單一文件內容可以產生多個程式碼內容，當文件使用範本，或包含檔案。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CDebugContext`物件，公開 \(expose\) [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。  
  
```cpp#  
HRESULT CDebugContext::EnumCodeContexts(IEnumDebugCodeContexts2 **ppEnumCodeCxts)    
{    
   HRESULT hr;    
  
   // Check for a valid IEnumDebugCodeContexts2 interface pointer.    
   if (ppEnumCodeCxts)    
   {    
      *ppEnumCodeCxts = NULL;    
  
      // Create a CEnumDebugCodeContexts object.    
      CComObject<CEnumDebugCodeContexts>* pEnum;    
      hr = CComObject<CEnumDebugCodeContexts>::CreateInstance(&pEnum);    
      assert(hr == S_OK);    
      if (hr == S_OK)    
      {    
         // Get an IID_IDebugCodeContext2 interface.    
         CComPtr<IDebugCodeContext2> spCodeCxt;    
         hr = QueryInterface(IID_IDebugCodeContext2,  
                             (void**)&spCodeCxt);  
         assert(hr == S_OK);    
         if (hr == S_OK)    
         {    
            // Initialize the code context enumerator with the    
            // IDebugCodeContext2 information.  
            IDebugCodeContext2* rgpCodeContext[] = { spCodeCxt.p };    
            hr = pEnum->Init(rgpCodeContext,  
                             &(rgpCodeContext[1]),  
                             NULL,  
                             AtlFlagCopy);  
            assert(hr == S_OK);    
            if (hr == S_OK)    
            {    
               // Set the passed IEnumDebugCodeContexts2 pointer equal to the pointer  
               // value of the created CEnumDebugCodeContexts object.  
               hr = pEnum->QueryInterface(ppEnumCodeCxts);    
               assert(hr == S_OK);    
            }    
         }    
  
         // Otherwise, delete the CEnumDebugCodeContexts object.    
         if (FAILED(hr))    
         {    
            delete pEnum;    
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
  
## 請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)