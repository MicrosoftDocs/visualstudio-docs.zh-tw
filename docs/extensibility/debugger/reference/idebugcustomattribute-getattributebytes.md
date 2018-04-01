---
title: IDebugCustomAttribute::GetAttributeBytes |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4cde5d8f27c7961e3b9ed7bda34473d755226072
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
取得 blob （位元組) 的屬性資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppBlob`  
 [in、 out]陣列，其中會填入屬性位元組。  
  
 `pdwLen`  
 [in、 out]指定要傳回的位元組數目上限`ppBlob`陣列並傳回實際寫入至陣列的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 設定`ppBlob`參數為 null 的值，傳回的數字屬性可用位元組。 配置陣列，然後將陣列中的傳送`ppBlob`參數。  
  
 屬性代表自訂屬性的未經處理資料。  
  
## <a name="see-also"></a>請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)