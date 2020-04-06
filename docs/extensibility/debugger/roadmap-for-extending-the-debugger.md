---
title: 擴展調試器的路線圖 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713139"
---
# <a name="roadmap-for-extending-the-debugger"></a>延伸除錯器的路線圖
本文檔提供有關 使用擴展調試[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]器的指南和參考[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]資訊。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試文檔包括範例、全面的參考和幾個具有代表性的方案,這些方案演示了自定義調試器的典型方法。

 編譯器及其輸出確定在產品中設置調試所需的內容。 如果編譯器:

- 以 Windows 本機作業系統為目標並寫入 *。PDB*檔案,您可以使用整合到的本機代碼除錯引擎 (DE)[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯程式 。 不需要實現 DE 或表達式賦值器。 表達式賦值器是為C++程式設計語言的語法而編寫的。

- 生成 Microsoft 中間語言 (MSIL) 輸出,您可以使用託管代碼調試引擎 DE 調[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]試程式,該引擎也集成到中。 因此,您只需要實現表達式賦值器。 為您提供一個範例表達式賦值器。 如需詳細資訊，請參閱下列主題：

   [運算運算](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [評估運算式](../../extensibility/debugger/evaluating-expressions.md)

   [運算式運算內容](../../extensibility/debugger/expression-evaluation-context.md)

   [中斷模式下的運算](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [編寫通用語言執行時表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- 以專有作業系統或其他運行時環境為目標,您需要編寫自己的 DE。 提供了一個教程,用於使用 ATL COM 創建簡單的 DE。 如需詳細資訊，請參閱下列主題：

   [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [教學:使用 ATL COM 建構除錯引擎](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [實施埠供應商](../../extensibility/debugger/implementing-a-port-supplier.md)

   [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>另請參閱
- [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
