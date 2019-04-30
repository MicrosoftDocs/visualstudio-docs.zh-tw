---
title: 偵錯工具內容 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fc77e24a1a9ca72d6f689247f0de6a9e0bf26cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889980"
---
# <a name="debugger-contexts"></a>偵錯工具內容
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯，偵錯引擎 (DE) 同時會在內部運作數種不同的內容，，如下所示：

- 程式碼內容，說明該應用程式的執行資料流中目前的位置。

- 文件內容的位置，其中描述來源文件中目前的位置。

- 運算式評估內容，描述要在哪一個運算式評估會發生的內容。

## <a name="in-this-section"></a>本節內容
 [程式碼內容](../../extensibility/debugger/code-context.md)討論程式碼內容，作為在現今的執行階段架構與非傳統任務為語言，其中的程式碼可能不會表示所需的指示，但其他方式的程式的指令資料流中的位址。

 [文件位置](../../extensibility/debugger/document-position.md)定義的 Visual Studio 偵錯透過原始程式檔中的某個位置的抽象概念，ide 中眾所周知的文件位置。

 [文件內容](../../extensibility/debugger/document-context.md)哪些文件內容代表 Visual Studio 偵錯原始程式檔相關的討論。 也會討論如何符號處理常式對應至文件內容的程式碼內容。

 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)提供 Visual Studio 中，運算式評估內容的相關資訊。 例如，堆疊框架相關聯的運算式評估內容提供的內容評估區域變數、 方法參數和類別成員。

## <a name="related-sections"></a>相關章節
 [偵錯概念](../../extensibility/debugger/debugger-concepts.md)描述主要的偵錯架構概念。

 [偵錯元件](../../extensibility/debugger/debugger-components.md)提供 Visual Studio 偵錯元件，包括偵錯引擎 (DE)、 運算式評估工具 (EE)，以及符號處理常式 (SH) 的概觀。

 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)包含各種偵錯工作，例如啟動程式和評估運算式的連結。