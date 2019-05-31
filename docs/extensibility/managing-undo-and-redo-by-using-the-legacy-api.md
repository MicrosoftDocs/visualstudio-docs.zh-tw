---
title: 管理復原和取消復原使用舊版 API |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a223d23cb792f13f1df9f869a540ffa61f50f9b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340637"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>管理復原和取消復原使用舊版的 API
編輯器必須支援可讓使用者反轉其最近的變更，它們就會修改程式碼時的復原作業。 大多數編輯器實作下[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可以自動提供整合式的開發環境 (IDE) 的復原支援。

## <a name="in-this-section"></a>本節內容
- [如何：實作復原管理](../extensibility/how-to-implement-undo-management.md)提供復原功能，可用於具有單一或多個檢視的編輯器。

- [如何：清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)說明如何清除復原堆疊。

- [如何：使用連結的復原管理](../extensibility/how-to-use-linked-undo-management.md)Incorporates 連結到您的編輯器復原管理。

## <a name="reference"></a>參考資料
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> 提供支援多個檢視的編輯器復原管理。
