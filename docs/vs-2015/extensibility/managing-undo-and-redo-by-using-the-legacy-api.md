---
title: 管理復原和取消復原使用舊版 API |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945148"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>管理的復原和重複使用舊版 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器必須支援可讓使用者反轉其最近的變更，它們就會修改程式碼時的復原作業。 大多數編輯器實作下[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]和[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]可以自動提供整合式的開發環境 (IDE) 的復原支援。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：實作復原管理](../extensibility/how-to-implement-undo-management.md)  
 編輯器提供復原功能，與單一或多個檢視。  
  
 [如何：清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)  
 說明如何清除復原堆疊。  
  
 [如何：使用連結的復原管理](../extensibility/how-to-use-linked-undo-management.md)  
 連結的復原管理併入您的編輯器。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 提供支援多個檢視的編輯器復原管理。  
  
## <a name="related-sections"></a>相關章節
