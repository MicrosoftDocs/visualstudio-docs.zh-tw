---
title: 開始使用除錯器延伸性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738601"
---
# <a name="get-started-with-debugger-extensibility"></a>開始使用除錯器擴充性
提供了[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]創建和自定義除錯元件所需的資訊,這些元件用於從[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境中調試程式。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試添加了從以前[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試器執行的廣泛可用性測試派生的改進。 您可以使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯來逐步完成多語言應用程式,也可以在除錯應用程式和多語言解決方案時實現變數的即時編輯。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試在行程外執行,程式正在調試,因此在應用程式的進程空間中的侵入性較小。 因此,編寫與調試器交互的元件會更容易,而不會影響調試程式。

 為了最好地使用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], 您應該熟悉以下項目:

- 整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]式開發環境

- C++程式設計語言

- ATL COM

## <a name="in-this-section"></a>本節內容
 [延伸除錯器的路線圖](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)概述在產品中實現調試的過程,具體取決於編譯器及其輸出。

 [除錯器元件](../../extensibility/debugger/debugger-components.md)提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試元件的概述,包括調試引擎 (DE)、表達式賦值器 (EE) 和符號處理程式 (SH)。

 [除錯器概念](../../extensibility/debugger/debugger-concepts.md)描述主要的調試體系結構概念。

 [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)說明除錯引擎 (DE) 如何在程式碼、文件和運算式評估上下文中同時執行。 描述三個上下文中的每一個與它相關的位置、位置或評估。

 [除錯工作](../../extensibility/debugger/debugging-tasks.md)包含指向各種除錯任務的連結,例如啟動程式和評估運算式。
