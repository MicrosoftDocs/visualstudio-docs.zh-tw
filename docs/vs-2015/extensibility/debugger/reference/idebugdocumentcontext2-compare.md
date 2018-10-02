---
title: IDebugDocumentContext2::Compare |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e100fdd8e303bf9a85e9ea8f7f0c77b6b300d8b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485833"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugDocumentContext2::Compare](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2-compare)。  
  
比較此文件內容，給定文件內容的陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `compare`  
 [in]值，以從[DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)列舉，指定的比較類型。  
  
 `rgpDocContextSet`  
 [in]陣列[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)代表所要比較的文件內容的物件。  
  
 `dwDocContextSetLen`  
 [in]要比較的文件內容的陣列的長度。  
  
 `pdwDocContext`  
 [out]傳回索引至`rgpDocContextSet`符合比較的第一個文件內容的陣列。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果找不到相符項目。 傳回`S_FALSE`如果找不到相符項目。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)陣列中傳遞的物件必須實作相同的偵錯引擎，可實作`IDebugDocumentContext2`物件所呼叫，否則比較無效。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)

