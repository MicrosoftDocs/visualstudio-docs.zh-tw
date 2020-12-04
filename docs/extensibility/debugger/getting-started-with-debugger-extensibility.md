---
title: 使用偵錯工具擴充性的消費者入門 |Microsoft Docs
description: 開始建立和自訂偵錯工具元件，以用於在 Visual Studio 環境內進行程式的偵錯工具。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6949b9b8a9168915c64bc6183f6b1391a1c79220
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560031"
---
# <a name="get-started-with-debugger-extensibility"></a>開始使用偵錯工具擴充性
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供您建立和自訂偵錯工具元件時所需的資訊，這些元件是用來從環境內進行程式的偵錯工具 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具已新增從先前偵錯工具上執行的廣泛可用性測試衍生的增強功能 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 您可以使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具來逐步執行多語言應用程式，也可以在對應用程式和多語言方案進行偵錯工具時，即時執行變數的編輯。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具是跨進程執行，且正在進行程式設計，因此不會干擾應用程式的進程空間。 因此，您可以更輕鬆地撰寫與偵錯工具互動的元件，而不會影響您的偵錯工具。

 若要充分使用 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ，您應該熟悉下列專案：

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 

- C + + 程式設計語言

- ATL COM

## <a name="in-this-section"></a>本節內容
 [擴充偵錯工具的藍圖](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) 概述在您的產品中執行偵錯工具的程式，取決於您的編譯器和其輸出。

 [偵錯工具元件](../../extensibility/debugger/debugger-components.md) 提供偵錯工具的總覽 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，包括 debug engine (DE) 、運算式評估工具 (EE) ，以及符號處理常式 (SH) 。

 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md) 描述主要的調試架構概念。

 [偵錯工具](../../extensibility/debugger/debugger-contexts.md) 內容說明 debug engine (DE) 如何在程式碼、檔和運算式評估內容中同時運作。 描述每個內容的相關位置、位置或評估。

 [調試作業](../../extensibility/debugger/debugging-tasks.md) 包含各種偵錯工具的連結，例如啟動程式和評估運算式。
