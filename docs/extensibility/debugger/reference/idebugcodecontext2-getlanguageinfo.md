---
title: "IDebugCodeContext2::GetLanguageInfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords: IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2b2f6f49b7ee8ebdf356a25bc2531aa2b8b9cf8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
取得這個程式碼內容的語言資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrLanguage`  
 [in、 out]傳回字串，包含名稱的語言，例如"C + +"。  
  
 `pguidLanguage`  
 [in、 out]例如，傳回之語言的程式碼內容中，GUID `guidCPPLang`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 至少其中一個參數必須傳回非 null 值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)