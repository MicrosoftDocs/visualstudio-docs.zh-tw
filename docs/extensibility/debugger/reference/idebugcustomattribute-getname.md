---
title: IDebugCustomAttribute::GetName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11a4b986799cf03221b4af077fc3e1e5809c4137
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866476"
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
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的具名會對應至用來宣告屬性的類別名稱。 因為 C# 可讓 [屬性] 後置詞，是要卸除從自訂屬性名稱在宣告中使用時，這並非完全可能對應至自訂屬性類別本身的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)