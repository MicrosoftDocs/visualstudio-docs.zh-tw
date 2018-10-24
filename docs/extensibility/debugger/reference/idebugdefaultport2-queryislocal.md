---
title: IDebugDefaultPort2::QueryIsLocal |Microsoft Docs
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
ms.openlocfilehash: 2ed411d632df544d47b376e59bc59b7331d8aa91
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901798"
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
 傳回`S_OK`此連接埠是否在本機 （在與呼叫端相同的電腦） 或`S_FALSE`連接埠是否位於另一部電腦上。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)