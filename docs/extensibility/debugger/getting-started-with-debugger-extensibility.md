---
title: 開始使用偵錯工具擴充性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98d6e0200c1a68ae3819d3276ce8a04aaada2e78
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-debugger-extensibility"></a>開始使用偵錯工具擴充性
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供的資訊，您必須建立和自訂用於偵錯程式中的偵錯工具元件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯已新增衍生自測試執行前一個廣泛的使用性增強功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具。 您可以使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯，以逐步執行多個語言的應用程式，或者您可以實作上即時偵錯應用程式和多語言方案時編輯的變數。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯是執行的跨處理正在偵錯的程式，因此較不干擾應用程式的處理序空間中。 因此，它是容易撰寫偵錯工具的互動的元件，而不會影響您偵錯的程式。  
  
 若要充分利用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，您應該熟悉下列：  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)  
  
-   C + + 程式設計語言  
  
-   ATL COM  
  
## <a name="in-this-section"></a>本節內容  
 [擴充偵錯工具的藍圖](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 概述實作您的產品，取決於您的編譯器和其輸出中的偵錯程的序。  
  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)  
 提供概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯元件，包括偵錯引擎 (DE)、 運算式評估工具 (EE)，以及符號處理常式 (SH)。  
  
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明如何偵錯引擎 (DE) 同時中運作的程式碼、 文件和運算式評估內容。 描述三個內容、 位置、 位置或評估適用於它的每個軸。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。