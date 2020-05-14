---
title: 可視化工作室調試器可擴充性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712505"
---
# <a name="visual-studio-debugger-extensibility"></a>視覺化工作室除錯器可擴充性
Visual Studio 包括一個完全互動式的原始程式碼偵錯器,提供了一個功能強大且易於使用的工具,用於追蹤程式中的 Bug。 除錯器完全支援視覺基本版、C#、C/C++ 和 JAvaScript。 但是,使用可從[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=21835)獲取的 ,調試器中可以支援其他程式設計語言,並具有相同的豐富功能。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試器是調試元件的通用前端(即用戶介面),而調試元件又特定於正在調試的語言。 對於新語言,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯器支援所需的只是建立必要的後端元件,如調試引擎 (DE)。 這一[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]點是進來的地方。

 包括[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]對創建新 DE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所需的所有 元素的完整引用。 此外,還有一些示例和教程將説明您入門。

 有關支援除錯的語言項目系統的完整範例,請參閱[IronPython 範例](https://www.microsoft.com/download/details.aspx?id=55984)。

 以下各節介紹如何使用擴展[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]調試器。

## <a name="in-this-section"></a>本節內容
 [開始](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)描述調試[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的內容以及如何安裝 SDK。

 [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)記錄自定義 DE 過程,從為 DE 準備程式到分離 DE。

 [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)說明是否必須編寫表達式賦值器。

 [選擇除錯引擎實施原則](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)討論如何實現DE。

 [參考文獻](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)記錄[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試 API。

 [樣品](../../extensibility/debugger/visual-studio-debugging-samples.md)包含指向通用語言運行時表達式賦值器範例和調試引擎範例的連結。
