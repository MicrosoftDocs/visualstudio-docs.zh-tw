---
title: 偵錯工具內容 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f36df39cf29ff298a327ec6e6d4bb02ff53485a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-contexts"></a>偵錯工具內容
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯，偵錯引擎 (DE) 運作方式同時在數種不同的內容，如下：  
  
-   程式碼內容，描述在程式的執行資料流中目前的位置。  
  
-   文件內容的位置，其中描述來源文件中目前的位置。  
  
-   運算式評估內容，描述要在哪一個運算式評估會發生的內容。  
  
## <a name="in-this-section"></a>本節內容  
 [程式碼內容](../../extensibility/debugger/code-context.md)  
 討論程式碼內容，為程式的指令資料流在現今的執行階段架構社會語言，與其中的程式碼可能不會顯示所需的指示，但其他方式的位址。  
  
 [文件位置](../../extensibility/debugger/document-position.md)  
 定義文件位置，在 Visual Studio 偵錯透過抽象概念的原始程式檔，因為知道在 IDE 中的位置。  
  
 [文件內容](../../extensibility/debugger/document-context.md)  
 討論在 Visual Studio 偵錯相對於原始程式檔中表示哪些文件內容。 也會討論如何符號處理常式對應至文件內容的程式碼內容。  
  
 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)  
 提供 Visual Studio 中，運算式評估內容相關資訊。 例如，堆疊框架相關聯的運算式評估內容提供內容評估本機變數、 方法參數和類別成員。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯元件](../../extensibility/debugger/debugger-components.md)  
 提供 Visual Studio 偵錯元件，包括偵錯引擎 (DE)、 運算式評估工具 (EE)，以及符號處理常式 (SH) 的概觀。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。