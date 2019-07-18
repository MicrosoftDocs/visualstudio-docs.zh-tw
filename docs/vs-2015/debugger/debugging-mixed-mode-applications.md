---
title: 偵錯混合模式應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c8e9f36e7118b1681701f6c8ac60a5bc851308f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691350"
---
# <a name="debugging-mixed-mode-applications"></a>偵錯混合模式應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

混合模式應用程式是指任何組合了機器碼 (C++) 和 Managed 程式碼 (例如在通用語言執行平台執行的 Visual Basic、Visual C# 或 C++) 的應用程式。 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中，偵錯混合模式應用程式是個極為平常的動作；這和偵錯單一模式應用程式大致上相同。 但是仍然要考慮一些特殊情況。  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>在混合模式偵錯中啟用 C++ 編輯後繼續  
  
- 若要在 Visual Studio 2013 中使用 C++ 的「編輯後繼續」，您必須還原成舊版偵錯引擎。 請參閱 Microsoft 應用程式生命週期管理部落格上的 [Switching to Managed Compatibility Mode in Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) (在 Visual Studio 2013 中切換成受控相容性模式)。  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>混合模式應用程式的屬性評估  
 在混合模式應用程式中，偵錯工具所進行的屬性評估是一種極耗資源的作業。 如此一來，像逐步執行之類的偵錯作業就會顯得相當慢。 如需詳細資訊，請參閱[逐步執行](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)。 如果您在混合模式偵錯的效能非常低，可以考慮關閉偵錯視窗的屬性評估。  
  
> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
#### <a name="to-turn-off-property-evaluation"></a>若要關閉屬性評估  
  
1. 在 [ **工具** ] 功能表上選擇 [ **選項**]。  
  
2. 在 [選項] 對話方塊中，開啟 [偵錯] 資料夾，並選取 [一般] 類別。  
  
3. 清除 [啟用屬性評估及其他隱含函式呼叫] 核取方塊。  
  
   因為原生呼叫堆疊和 Managed 呼叫堆疊有所不同，偵錯工具無法一直為混合模式提供完整呼叫堆疊。 當機器碼呼叫 Managed 程式碼時，您可能會發現某些不一樣的地方。 如需詳細資訊，請參閱[呼叫堆疊視窗內混合程式碼和遺失的資訊](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
