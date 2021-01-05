---
title: Mixed-Mode 應用程式的偵錯工具 |Microsoft Docs
description: 在 Visual Studio 中，調試混合模式應用程式，此應用程式會結合機器碼與 common language runtime 上執行的 managed 程式碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4137e7a73032a34276416b9640dd608b96b660a4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728326"
---
# <a name="debugging-mixed-mode-applications"></a>偵錯混合模式應用程式
混合模式應用程式是指任何組合了機器碼 (C++) 和 Managed 程式碼 (例如在通用語言執行平台執行的 Visual Basic、Visual C# 或 C++) 的應用程式。 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，偵錯混合模式應用程式是個極為平常的動作；這和偵錯單一模式應用程式大致上相同。 但是仍然要考慮一些特殊情況。

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>在混合模式偵錯中啟用 C++ 編輯後繼續

若要啟用 c + + 的 [編輯後繼續]，請參閱 [如何啟用和停](../debugger/how-to-enable-and-disable-edit-and-continue.md)用 [編輯後繼續]。

> [!NOTE]
> 若要在 Visual Studio 2013 中使用 C++ 的「編輯後繼續」，您必須還原成舊版偵錯引擎。 請參閱 Microsoft 應用程式生命週期管理部落格上的 [Switching to Managed Compatibility Mode in Visual Studio 2013](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) (在 Visual Studio 2013 中切換成受控相容性模式)。

## <a name="property-evaluation-in-mixed-mode-applications"></a>混合模式應用程式的屬性評估
 在混合模式應用程式中，偵錯工具所進行的屬性評估是一種極耗資源的作業。 如此一來，像逐步執行之類的偵錯作業就會顯得相當慢。 如需詳細資訊，請參閱[逐步執行](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100))。 如果您在混合模式偵錯的效能非常低，可以考慮關閉偵錯視窗的屬性評估。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

### <a name="to-turn-off-property-evaluation"></a>若要關閉屬性評估

1. 在 [工具] 功能表上，選擇 [選項]。

2. 在 [選項] 對話方塊中，開啟 [偵錯] 資料夾，並選取 [一般] 類別。

3. 清除 [啟用屬性評估及其他隱含函式呼叫] 核取方塊。

   因為原生呼叫堆疊和 Managed 呼叫堆疊有所不同，偵錯工具無法一直為混合模式提供完整呼叫堆疊。 當機器碼呼叫 Managed 程式碼時，您可能會發現某些不一樣的地方。 如需詳細資訊，請參閱[呼叫堆疊視窗內混合程式碼和遺失的資訊](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)。

## <a name="see-also"></a>請參閱

- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)