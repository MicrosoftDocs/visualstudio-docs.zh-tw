---
title: IDebugGenericFieldInstance |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ab9c43e915f2c23dfe5f38ce61beff29949ca0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180794"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

表示欄位的 managed 程式碼的泛型型別執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## <a name="methods"></a>方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|擷取這個執行個體的型別參數引數。|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|傳回類型的數目參數引數，這個執行個體。|  
  
## <a name="requirements"></a>需求  
 標頭：Sh.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll
