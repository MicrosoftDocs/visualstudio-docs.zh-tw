---
title: "管理復原和取消復原使用舊版 API |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41672845d318707512472f556753f429661d008c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>管理復原和取消復原使用舊版 API
編輯器必須支援，讓使用者可以反轉最近的變更，它們就會修改程式碼時的復原作業。 大部分的編輯器下實作[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可以自動提供整合式的開發環境 (IDE) 的復原支援。  
  
## <a name="in-this-section"></a>本章節內容  
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