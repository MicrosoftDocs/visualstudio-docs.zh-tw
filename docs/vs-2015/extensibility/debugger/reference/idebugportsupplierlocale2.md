---
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 789d9f97958b9662db5f792f28a75c0f6b46a8c8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188157"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

提供連接埠提供者的地區設定支援。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 自訂的連接埠提供者會實作這個介面來設定的地區設定。  
  
## <a name="methods"></a>方法  
 下表顯示的方法**IDebugPortSupplierLocale2**。  
  
|方法|描述|  
|------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|設定連接埠提供者的地區設定。|  
  
## <a name="requirements"></a>需求  
 標頭：Portpriv.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
