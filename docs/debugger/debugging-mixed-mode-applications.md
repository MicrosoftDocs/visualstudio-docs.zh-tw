---
title: 偵錯混合模式應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f06a1da269fec2cf1966b17b9497e840808b6c73
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887614"
---
# <a name="debugging-mixed-mode-applications"></a>偵錯混合模式應用程式
混合模式應用程式是指任何組合了機器碼 (C++) 和 Managed 程式碼 (例如在通用語言執行平台執行的 Visual Basic、Visual C# 或 C++) 的應用程式。 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，偵錯混合模式應用程式是個極為平常的動作；這和偵錯單一模式應用程式大致上相同。 但是仍然要考慮一些特殊情況。  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>在混合模式偵錯中啟用 C++ 編輯後繼續  

若要啟用 c + + 編輯後繼續，請參閱[如何啟用和停用編輯後繼續](../debugger/how-to-enable-and-disable-edit-and-continue.md)。

> [!NOTE]
> 若要在 Visual Studio 2013 中使用 C++ 的「編輯後繼續」，您必須還原成舊版偵錯引擎。 請參閱[切換至 Visual Studio 2013 中的 Managed 相容性模式](https://blogs.msdn.microsoft.com/devops/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013/)Microsoft Application Lifecycle Management 部落格上。  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>混合模式應用程式的屬性評估  
 在混合模式應用程式中，偵錯工具所進行的屬性評估是一種極耗資源的作業。 如此一來，像逐步執行之類的偵錯作業就會顯得相當慢。 如需詳細資訊，請參閱 <<c0> [ 逐步執行程式碼](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100))。 如果您在混合模式偵錯的效能非常低，可以考慮關閉偵錯視窗的屬性評估。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
#### <a name="to-turn-off-property-evaluation"></a>若要關閉屬性評估  
  
1. 在 [ **工具** ] 功能表上選擇 [ **選項**]。  
  
2. 在 **選項**對話方塊中，開啟**偵錯**資料夾，然後選取**一般**類別目錄。  
  
3. 清除**啟用屬性評估及其他隱含函式呼叫**核取方塊。  
  
   因為原生呼叫堆疊和 Managed 呼叫堆疊有所不同，偵錯工具無法一直為混合模式提供完整呼叫堆疊。 當機器碼呼叫 Managed 程式碼時，您可能會發現某些不一樣的地方。 如需詳細資訊，請參閱 <<c0> [ 混合程式碼和遺失的資訊，請在 [呼叫堆疊] 視窗中](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)