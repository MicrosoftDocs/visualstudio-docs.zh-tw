---
title: IDebugDefaultPort2::QueryIsLocal |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cec66860bb75cb62e71e2924ed728e1bd86ad59f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
這個方法會判斷此連接埠是否在本機電腦上。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`此連接埠是否為本機 （在呼叫端相同的電腦） 或`S_FALSE`連接埠是否位於另一部電腦上。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)