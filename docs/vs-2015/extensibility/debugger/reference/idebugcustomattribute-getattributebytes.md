---
title: IDebugCustomAttribute：： GetAttributeBytes |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7813e8e3131b04dc7174b5b666950dd68a6060a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569064"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得以位元組 blob 表示的屬性資訊。  
  
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
 [in，out]以屬性位元組填入的陣列。  
  
 `pdwLen`  
 [in，out]指定要在陣列中傳回的最大位元組數目 `ppBlob` ，並傳回實際寫入陣列的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 將 `ppBlob` 參數設定為 null 值，以傳回可用的屬性位元組數目。 然後配置陣列，並針對參數傳遞該陣列 `ppBlob` 。  
  
 屬性位元組代表自訂屬性的原始資料。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
