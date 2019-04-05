---
title: IDebugPortSupplier2::GetPort | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c86af9f78d66abb0b7e4020c7f4ee2e7405ad68
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945668"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從連接埠提供者取得的連接埠。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidPort`  
 [in]連接埠的全域唯一識別碼 (GUID)。  
  
 `ppPort`  
 [out]傳回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示連接埠。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_PORTSUPPLIER_NO_PORT`如果沒有連接埠存在具有指定識別項。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
