---
title: 擴充偵錯工具藍圖 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e02bfd8b528c484518816589f4f3e0e19bfa8c94
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687519"
---
# <a name="roadmap-for-extending-the-debugger"></a>擴充偵錯工具的藍圖
這份文件提供用於擴充的指南和參考資訊[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]偵錯工具與[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯文件包含範例、 完整的參考，並示範一般的方式來自訂偵錯工具的幾個代表性案例。

 您的編譯器和其輸出會決定設定您的產品中的偵錯的必要條件。 如果您的編譯器：

- 以 Windows 原生作業系統為目標，並將寫入 *。PDB*檔案中，您可以使用偵錯程式原生程式碼的偵錯引擎 (DE)，已整合至[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您不需要實作 DE 或運算式的評估工具。 運算式評估工具是針對 c + + 程式設計語言的語法所撰寫。

- 產生的 Microsoft intermediate language (MSIL) 的輸出，您可以使用 managed 程式碼的偵錯引擎 DE，這也會整合到偵錯程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，您只需要實作的運算式評估工具。 為您提供的範例運算式評估工具。 如需詳細資訊，請參閱下列主題：

   [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [評估運算式](../../extensibility/debugger/evaluating-expressions.md)

   [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)

   [在中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [撰寫 common language runtime 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- 作業系統或某些其他執行階段環境的專屬的目標，您需要撰寫您自己的裝置。 建立簡單的規定，使用 ATL COM 的教學課程會提供。 如需詳細資訊，請參閱下列主題：

   [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [教學課程：建置使用 ATL COM 偵錯引擎](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)

   [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>另請參閱
- [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)