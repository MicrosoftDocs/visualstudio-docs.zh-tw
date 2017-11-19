---
title: "IDebugPortSupplierDescription2::GetDescription |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortSupplierDescription2::GetDescription
ms.assetid: bff5f536-1cd1-4313-8856-db7b05818305
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d281ae3b069eb3644e57b82581cc3f5b51a7b0c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplierdescription2getdescription"></a>IDebugPortSupplierDescription2::GetDescription
擷取連接埠供應商的描述和描述中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDescription(  
   PORT_SUPPLIER_DESCRIPTION_FLAGS *pdwFlags,  
   BSTR *pbstrText  
);  
```  
  
```csharp  
public int GetDescription(  
   out enum_PORT_SUPPLIER_DESCRIPTION_FLAGS pdwFlags,  
   out string pbstrText  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwFlags`  
 [out]描述中繼資料旗標。  
  
 `pbstrText`  
 [out]連接埠供應商的描述。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)