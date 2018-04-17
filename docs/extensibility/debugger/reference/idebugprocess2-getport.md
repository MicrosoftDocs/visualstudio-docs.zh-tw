---
title: IDebugProcess2::GetPort |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2bbfcd8b53f1f864fc7463a9a07c556a334bb59f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
取得處理程序執行的連接埠。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPort(   
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppPort`  
 [out]傳回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示啟動處理程序所在的連接埠。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)