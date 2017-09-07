---
title: "IDebugProgramPublisher2::PublishProgram |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3f573f35ed0130eb020ac2e8e19a0391050ec06e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
這個方法可供使用的偵錯引擎 (DEs) 程式，偵錯工作階段管理員。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>參數  
 `Engines`  
 [in]對於 DEs，可以啟動或附加至這個程式的 Guid 陣列。  
  
 `szFriendlyName`  
 [in]（這會出現在功能表或對話方塊呈現給使用者） 程式的易記名稱。  
  
 `pDebuggeeInterface`  
 [in]`IUnknown`程式介面 （來唯一識別該程式使用此值作為 cookie;"取消發行 」 程式會使用此相同的值）  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要讓程式不再適用於偵錯，呼叫[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
