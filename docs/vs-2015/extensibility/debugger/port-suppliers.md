---
title: 連接埠供應商 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8ca5c7d9154b07cbc51b5fde6b9c85e97d880df
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751584"
---
# <a name="port-suppliers"></a>連接埠提供者
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯工具就架構而言，**連接埠提供者**:  
  
- 包含由伺服器，並提供連接埠上對該伺服器的要求。  
  
- 新增和移除，其中包含伺服器的連接埠。  
  
- 可以列舉它已提供給伺服器的所有連接埠。  
  
- 由[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面，透過登錄向 Visual Studio。 這個介面，可由呼叫[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)。  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 提供的預設連接埠提供者和預設連接埠。 如果需要實作自訂連接埠，自訂連接埠供應商也必須實作以提供這些自訂的連接埠。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [連接埠](../../extensibility/debugger/ports.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

