---
title: IDebugObject2::GetBackingFieldForProperty |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10f6c5b8a3da4539bfbe2efce23bd29a10f257ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283552"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得變數的欄位 （如果有的話），可能會支援這個物件所表示的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppObject`  
 [out][IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件，描述支援欄位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件代表 managed 程式碼類別屬性，也就是使用 get 方法和 （或) set 存取子。 這類屬性通常會需要一個變數能夠容納操作屬性的值。 這個變數就是所謂的支援欄位。 如果物件不支援欄位，請務必傳回 null 值： 有些呼叫端可能會不注意傳回的值，但將會改為查看中已傳回了 null 值`ppObject`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

