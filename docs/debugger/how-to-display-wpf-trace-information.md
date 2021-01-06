---
title: 顯示 WPF 追蹤資訊 |Microsoft Docs
description: Visual Studio 可以從 WPF 應用程式接收偵錯工具追蹤資訊，並將其顯示在 [輸出] 視窗中。 瞭解如何管理和自訂 WPF 追蹤。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4800c2ca44c2c52b2059685d9c5bc4fe38ed08
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903970"
---
# <a name="how-to-display-wpf-trace-information"></a>如何：顯示 WPF 追蹤資訊
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 可以從 WPF 應用程式接收偵錯追蹤資訊，並將該資訊顯示在 [輸出] 視窗中。 若要顯示偵錯追蹤資訊，則必須啟用 WPF 追蹤功能。

 您可以在 App.Config 檔中啟用 WPF 追蹤功能，或是使用 <xref:System.Diagnostics.PresentationTraceSources> 類別以程式設計的方式加以啟用。 使用 [選項] 視窗比較容易啟用 WPF 追蹤功能。 不支援使用 Web 應用程式的 WPF 追蹤。

### <a name="to-enable-or-customize-wpf-trace-information"></a>若要啟用或自訂 WPF 追蹤資訊

1. 在 [工具] 功能表上，選取 [選項]。

2. 在 [選項] 對話方塊中，開啟左邊方塊中的 [偵錯] 節點。

3. 按一下 [偵錯] 下方的 [輸出視窗]。

4. 選取 [一般輸出設定] 下的 [所有偵錯輸出]。

5. 在右側方塊中，尋找 [WPF 追蹤設定]。

6. 開啟 [WPF 追蹤設定] 節點。

7. 在 [WPF 追蹤設定] 下方，按一下您想要啟用的設定分類 (例如 [資料繫結])。

     您所按的 [資料繫結] 或任何分類旁的 [設定] 欄中都會出現一個下拉式清單控制項。

8. 按一下下拉式清單，並選取您想要查看的追蹤資訊類型：[全部]、[重大]、[錯誤]、[警告]、[資訊]、[詳細資訊] 或 [ActivityTracing]。

     [重要] 僅限追蹤重要事件。

     [錯誤] 能夠追蹤重要和錯誤事件。

     [警告] 能夠追蹤重要、錯誤和警告事件。

     [資訊] 能夠追蹤重要、錯誤、警告和資訊事件。

     [詳細資訊] 能夠追蹤重要、錯誤、警告、資訊和詳細資訊事件。

     [ActivityTracing] 能夠追蹤停止、開始、暫停、傳輸 和繼續事件。

     如需這些追蹤資訊層級含意的詳細資訊，請參閱 <xref:System.Diagnostics.SourceLevels>。

9. 按一下 [確定]。

### <a name="to-disable-wpf-trace-information"></a>若要停用 WPF 追蹤資訊

1. 在 [工具] 功能表上，選取 [選項]。

2. 在 [選項] 對話方塊中，開啟左邊方塊中的 [偵錯] 節點。

3. 按一下 [偵錯] 下方的 [輸出視窗]。

4. 在右側方塊中，尋找 [WPF 追蹤設定]。

5. 開啟 [WPF 追蹤設定] 節點。

6. 在 [WPF 追蹤設定] 下方，按一下您想要啟用的設定分類 (例如 [資料繫結])。

     您所按的 [資料繫結] 或任何分類旁的 [設定] 欄中都會出現一個下拉式清單控制項。

7. 按一下此下拉式清單，然後選取 [關閉]。

8. 按一下 [確定]。

## <a name="see-also"></a>另請參閱
- [偵錯 WPF](../debugger/debugging-wpf.md)