---
title: 偵錯工具概念 |Microsoft Docs
description: 瞭解設計 Visual Studio debug 封裝時所使用的架構概念，以協助您建立該套件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5202ebdb621121e63adbdf5118cb0848689adde6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952404"
---
# <a name="debugger-concepts"></a>偵錯工具概念
若要建立 Visual Studio 的 debug 封裝，您必須熟悉設計封裝時所使用的架構概念。

## <a name="in-this-section"></a>本節內容
 [Debug 會話](../../extensibility/debugger/debug-session.md) 說明在偵錯工具架構中會話的角色。

 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md) 以抽象和實體詞彙定義伺服器在偵錯工具架構方面的意義。

 [埠供應商](../../extensibility/debugger/port-suppliers.md) 定義埠供應商在偵測架構方面的意義。

 [埠](../../extensibility/debugger/ports.md) 定義埠在偵錯工具架構方面的意義。

 [進程](../../extensibility/debugger/processes.md) 定義處理常式在偵測架構方面的意義。

 [程式節點](../../extensibility/debugger/program-nodes.md) 根據偵測架構來定義程式節點，包括它本身的識別方式，以及其執行所在的進程。

 [程式](../../extensibility/debugger/programs.md) 根據偵錯工具架構來定義程式。

 [執行緒](../../extensibility/debugger/threads.md) 定義執行緒在偵錯工具架構方面的特性。

 [堆疊框架](../../extensibility/debugger/stack-frames.md) 根據偵錯工具架構來定義堆疊框架。 堆疊框架是堆疊的抽象概念，可提供執行緒的執行內容。

 [模組](../../extensibility/debugger/modules.md) 將模組以偵錯工具架構的形式定義為程式碼的實體容器，例如可執行檔或 DLL。

 [中斷點](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) 根據偵測架構，定義三種類型的中斷點，包括暫止、系結和錯誤。

## <a name="related-sections"></a>相關章節
 [偵錯工具](../../extensibility/debugger/debugger-contexts.md) 內容說明 debug engine (DE) 如何在程式碼、檔和運算式評估內容中同時運作。 描述每個內容的相關位置、位置或評估。

 [偵錯工具元件](../../extensibility/debugger/debugger-components.md) 概要說明 Visual Studio 的偵錯工具元件，其中包括 debug engine (DE) 、運算式評估工具 (EE) ，以及符號處理常式 (SH) 。

 [調試作業](../../extensibility/debugger/debugging-tasks.md) 包含各種偵錯工具的連結，例如啟動程式和評估運算式。
