---
title: IDebugPortSupplierEx2::SetServer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2::SetServer
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f20fd2bdb54faa8c6a8aaf407a70c97c9f9af55f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188168"
---
# <a name="idebugportsupplierex2setserver"></a>IDebugPortSupplierEx2::SetServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

設定核心伺服器連接埠提供者。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT SetServer(  
   IDebugCoreServer2* pServer  
);  
```  
  
```csharp  
int SetServer(  
   IDebugCoreServer2 pServer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pServer`  
 若要設定連接埠提供者的核心伺服器。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)
