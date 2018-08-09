---
title: 管理復原和取消復原使用舊版 API |Microsoft Docs
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
ms.openlocfilehash: be60b3f0dd45a40663770b4b0debe8023e277f32
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638068"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>管理復原和取消復原使用舊版的 API
編輯器必須支援可讓使用者反轉其最近的變更，它們就會修改程式碼時的復原作業。 大多數編輯器實作下[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可以自動提供整合式的開發環境 (IDE) 的復原支援。  
  
## <a name="in-this-section"></a>本節內容  
 [如何： 實作復原管理](../extensibility/how-to-implement-undo-management.md)  
 編輯器提供復原功能，與單一或多個檢視。  
  
 [如何： 清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)  
 說明如何清除復原堆疊。  
  
 [如何： 使用連結復原管理](../extensibility/how-to-use-linked-undo-management.md)  
 連結的復原管理併入您的編輯器。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 提供支援多個檢視的編輯器復原管理。  
