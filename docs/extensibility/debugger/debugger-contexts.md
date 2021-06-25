---
title: 偵錯工具內容 |Microsoft Docs
description: 瞭解 Visual Studio debug engine 如何在不同的內容中運作：程式碼內容、檔內容或位置，以及運算式評估內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5103561a420c3836f60a22790335522a83798966
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903667"
---
# <a name="debugger-contexts"></a>偵錯工具內容
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 調試中，debug engine (DE) 在數個不同的內容中同時運作，如下所示：

- 程式碼內容，描述程式執行資料流程中的目前位置。

- 檔內容或位置，描述來源文件中的目前位置。

- 運算式評估內容，描述將在其中進行運算式評估的內容。

## <a name="in-this-section"></a>本節內容
 程式[代碼內容](../../extensibility/debugger/code-context.md)在目前的執行時間架構與非傳統語言中，將程式碼內容討論為程式指令資料流程中的位址，其中程式碼可能不會以指示表示，但還有其他方法。

 [檔位置](../../extensibility/debugger/document-position.md) 藉由在原始程式檔中的位置抽象化（如 IDE 已知）來定義 Visual Studio 的檔位置。

 [檔內容](../../extensibility/debugger/document-context.md) 討論與原始檔相關的 Visual Studio 錯錯中的檔內容。 此外也會討論符號處理常式如何將程式碼內容對應至檔內容。

 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md) 提供 Visual Studio 中運算式評估內容的相關資訊。 例如，與堆疊框架相關聯的運算式評估內容會提供用來評估區域變數、方法參數和類別成員的內容。

## <a name="related-sections"></a>相關章節
 [Debug 概念](../../extensibility/debugger/debugger-concepts.md) 描述主要的調試架構概念。

 [Debug 元件](../../extensibility/debugger/debugger-components.md) 概要說明 Visual Studio 的偵錯工具元件，其中包括 debug engine (DE) 、運算式評估工具 (EE) ，以及符號處理常式 (SH) 。

 [調試作業](../../extensibility/debugger/debugging-tasks.md) 包含各種偵錯工具的連結，例如啟動程式和評估運算式。
