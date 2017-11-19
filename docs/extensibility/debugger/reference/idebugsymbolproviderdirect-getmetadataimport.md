---
title: "IDebugSymbolProviderDirect::GetMetaDataImport |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetMetaDataImport
- IDebugSymbolProviderDirect::GetMetaDataImport
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f35e76579a93dfc83454322699325e1dfec09734
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolproviderdirectgetmetadataimport"></a>IDebugSymbolProviderDirect::GetMetaDataImport
擷取中繼資料匯入資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```csharp  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]模組的唯一識別碼。  
  
 `appID`  
 [in]應用程式定義域的識別項。  
  
 `ppImport`  
 [out]傳回物件，其中包含中繼資料匯入資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)