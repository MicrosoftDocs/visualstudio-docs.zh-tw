---
title: 管理復原和取消復原使用舊版 API |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93bb65fa9865c5ca7386925d2c145f2acbc0993a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137507"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>管理復原和取消復原使用舊版 API
編輯器必須支援，讓使用者可以反轉最近的變更，它們就會修改程式碼時的復原作業。 大部分的編輯器下實作[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可以自動提供整合式的開發環境 (IDE) 的復原支援。  
  
## <a name="in-this-section"></a>本節內容  
 [如何： 實作復原管理](../extensibility/how-to-implement-undo-management.md)  
 與單一或多個檢視提供編輯器復原功能。  
  
 [如何： 清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)  
 描述如何清除復原堆疊。  
  
 [如何： 使用已連結的復原管理](../extensibility/how-to-use-linked-undo-management.md)  
 您的編輯器中納入已連結的復原管理。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 提供支援多個檢視的編輯器復原管理。  
  
## <a name="related-sections"></a>相關章節