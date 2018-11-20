---
title: 偵錯工具內容 |Microsoft Docs
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
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b39e53ab06d3ce1633a77fc1fe324206f144dda1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793538"
---
# <a name="debugger-contexts"></a>偵錯工具內容
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯，偵錯引擎 (DE) 同時會在內部運作數種不同的內容，，如下所示：  
  
-   程式碼內容，說明該應用程式的執行資料流中目前的位置。  
  
-   文件內容的位置，其中描述來源文件中目前的位置。  
  
-   運算式評估內容，描述要在哪一個運算式評估會發生的內容。  
  
## <a name="in-this-section"></a>本節內容  
 [程式碼內容](../../extensibility/debugger/code-context.md)  
 在現今的執行階段架構與非傳統任務為語言，其中的程式碼可能不會表示所需的指示，但其他方式的程式的指令資料流中的地址為討論程式碼內容。  
  
 [文件位置](../../extensibility/debugger/document-position.md)  
 定義在 Visual Studio 偵錯中透過 ide 中眾所周知的原始程式檔中的某個位置的抽象概念的文件位置。  
  
 [文件內容](../../extensibility/debugger/document-context.md)  
 討論哪些文件內容代表 Visual Studio 偵錯相對於原始程式檔中。 也會討論如何符號處理常式對應至文件內容的程式碼內容。  
  
 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)  
 提供在 Visual Studio 中，運算式評估內容的相關資訊。 例如，堆疊框架相關聯的運算式評估內容提供的內容評估區域變數、 方法參數和類別成員。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯元件](../../extensibility/debugger/debugger-components.md)  
 提供 Visual Studio 偵錯元件，包括偵錯引擎 (DE)、 運算式評估工具 (EE)，以及符號處理常式 (SH) 的概觀。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。

