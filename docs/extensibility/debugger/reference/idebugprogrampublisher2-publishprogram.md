---
title: "IDebugProgramPublisher2::PublishProgram |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramPublisher2::PublishProgram
helpviewer_keywords: IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bcf9ee09a05e2de89a57670969325a8105fa014
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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