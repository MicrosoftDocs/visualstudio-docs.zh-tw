---
title: IDebugCustomAttribute::GetAttributeBytes |Microsoft Docs
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
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 574deb12fd774d989f2868dd1300c6a641849015
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489792"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugCustomAttribute::GetAttributeBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattribute-getattributebytes)。  
  
取得屬性資訊為 blob (位元組）。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in、 out]陣列，其中會填入屬性的位元組。  
  
 `pdwLen`  
 [in、 out]指定要傳回的位元組數目上限`ppBlob`陣列並傳回實際寫入至陣列的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 設定`ppBlob`參數為 null 的值，傳回的數字屬性可用位元組。 配置的陣列，然後將陣列中的傳送`ppBlob`參數。  
  
 屬性代表的原始資料的自訂屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

