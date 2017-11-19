---
title: "IDebugCustomAttribute::GetName |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetName
helpviewer_keywords: IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 165362ab03685a3acca457e4095778b9dcb182e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
取得自訂屬性的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bstrName`  
 [out]傳回字串，包含自訂屬性的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的具名會對應至用來宣告屬性類別的名稱。 這可能不完全對應到名稱自訂屬性類別本身的 C# 允許 「 屬性 」 尾碼，用於在宣告時卸除從自訂屬性的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)