---
title: "IDebugProgram2::GetDebugProperty |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetDebugProperty
helpviewer_keywords: IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86328e07b8cd2cf8c72de5713b347512f4a354c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
取得程式的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppProperty`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示程式的內容。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的屬性專屬於該程式。 如果程式需要傳回多個屬性，則[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)這個方法所傳回的物件是容器的其他屬性和呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)方法會傳回所有屬性的清單。  
  
 程式可能會公開任何數量和類型的其他屬性，可以透過描述`IDebugProperty2`介面。 IDE 可能會顯示透過泛型屬性瀏覽器使用者介面的其他程式屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)