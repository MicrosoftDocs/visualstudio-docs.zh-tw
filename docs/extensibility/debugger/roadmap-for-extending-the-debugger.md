---
title: 擴充偵錯工具的藍圖 |Microsoft Docs
description: Visual Studio 的偵錯工具包括範例、參考和數個示範自訂偵錯工具之一般方式的案例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be0f746a849a8370b145a46f9fbf6340a1dc98fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961075"
---
# <a name="roadmap-for-extending-the-debugger"></a>擴充偵錯工具的藍圖
本檔提供使用擴充偵錯工具的指南和參考資訊 [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具檔包括範例、完整參考和數個代表性案例，示範自訂偵錯工具的一般方式。

 您的編譯器和其輸出會決定在您的產品中設定偵錯工具所需的內容。 如果您的編譯器：

- 以 Windows 原生作業系統為目標，並寫入 *。PDB* 檔案，您可以使用原生程式碼的偵錯工具引擎來進行程式碼偵測引擎的 (DE) （整合至） [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 您不需要執行 DE 或運算式評估工具。 運算式評估工具是針對 c + + 程式設計語言的語法所撰寫的。

- 產生 Microsoft 中繼語言 (MSIL) 輸出，您可以使用也整合至的 managed 程式碼偵測引擎 DE 來進行程式碼的偵錯工具 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 因此，您只需要執行運算式評估工具。 系統會為您提供範例運算式評估工具。 如需詳細資訊，請參閱下列主題：

   [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [評估運算式](../../extensibility/debugger/evaluating-expressions.md)

   [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)

   [中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [撰寫 common language runtime 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- 以專屬的作業系統或其他執行時間環境為目標，您必須自行撰寫 DE。 提供使用 ATL COM 建立簡單 DE 的教學課程。 如需詳細資訊，請參閱下列主題：

   [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [教學課程：使用 ATL COM 建立 debug engine](/previous-versions/bb147024(v=vs.90))

   [執行埠供應商](../../extensibility/debugger/implementing-a-port-supplier.md)

   [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>另請參閱
- [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)