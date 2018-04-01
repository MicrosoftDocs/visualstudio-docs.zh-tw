---
title: IDebugDocumentText2::GetSize |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 117d557ad2ee5d7fe3490644162d1995e86c1873
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
擷取文件中的此位置的文字的大小。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcNumLines`  
 [out]傳回的文字行數。  
  
 `pcNumChars`  
 [out]傳回文字的字元數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [只有 c + +]如果不需要特定的值，傳遞參數為 NULL。  
  
 [僅限 C#]必須指定這兩個參數。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)