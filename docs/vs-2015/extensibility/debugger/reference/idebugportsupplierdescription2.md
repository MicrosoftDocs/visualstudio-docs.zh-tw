---
title: IDebugPortSupplierDescription2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 042cb2090f87a3b1453f31a833c584f7d30e5a13
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484967"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugPortSupplierDescription2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplierdescription2)。  
  
可讓[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI，以顯示內部文字**傳輸資訊**一節**附加至處理序** 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 連接埠提供者會實作這個介面。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugPortSupplierDescription2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|擷取連接埠提供者的描述和描述中繼資料。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

