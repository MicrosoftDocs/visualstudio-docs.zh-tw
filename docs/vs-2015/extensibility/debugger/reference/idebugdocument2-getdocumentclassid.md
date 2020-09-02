---
title: IDebugDocument2：： GetDocumentClassID |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ac97400d09e77b0910b945d78c2f0cf28073a01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186667"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得檔的類別識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```csharp  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pclsid`  
 擴展傳回 GUID，也就是檔的類別識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 類別 GUID 可以用來具現化個別類別，每個類別都代表一個檔。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
