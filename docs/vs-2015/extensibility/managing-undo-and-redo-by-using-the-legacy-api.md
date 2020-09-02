---
title: 使用舊版 API 管理復原和重做 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194363"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>使用舊版 API 管理復原和重做
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器必須支援可讓使用者在修改程式碼時反轉其最近變更的復原作業。 在和下執行的大部分編輯器都 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 可以 (IDE) ，由整合式開發環境自動提供復原支援。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：實作復原管理](../extensibility/how-to-implement-undo-management.md)  
 為具有單一或多個視圖的編輯器提供復原功能。  
  
 [如何：清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)  
 說明如何清除復原堆疊。  
  
 [如何：使用連結的復原管理](../extensibility/how-to-use-linked-undo-management.md)  
 將連結的復原管理併入編輯器中。  
  
## <a name="reference"></a>參考  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 提供支援多個視圖之編輯器的復原管理。  
  
## <a name="related-sections"></a>相關章節
