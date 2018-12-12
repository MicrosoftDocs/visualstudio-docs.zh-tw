---
title: 如何： 顯示 WPF 追蹤資訊 |Microsoft 文件
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
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99fc861c627a094f9f5e4e67a6b034ecdd407688
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476220"
---
# <a name="how-to-display-wpf-trace-information"></a>如何：顯示 WPF 追蹤資訊
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 可以從 WPF 應用程式接收偵錯追蹤資訊，並顯示該資訊**輸出**視窗。 若要顯示偵錯追蹤資訊，必須啟用 WPF 追蹤。  
  
 您可以在 App.Config 檔中啟用 WPF 追蹤功能，或是使用 <xref:System.Diagnostics.PresentationTraceSources> 類別以程式設計的方式加以啟用。 若要啟用 WPF 追蹤更簡單的方法是使用**選項**視窗。 不支援使用 Web 應用程式的 WPF 追蹤。  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>若要啟用或自訂 WPF 追蹤資訊  
  
1.  在 [工具] 功能表上，選取 [選項]。  
  
2.  在**選項**對話方塊的左側方塊中開啟**偵錯**節點。  
  
3.  在下**偵錯**，按一下 [**輸出] 視窗**。  
  
4.  在下**一般輸出設定**，選取**所有偵錯輸出**。  
  
5.  在右邊方塊中，尋找**WPF 追蹤設定**。  
  
6.  開啟**WPF 追蹤設定**節點。  
  
7.  在下**WPF 追蹤設定**，按一下您想要啟用的設定類別 (例如，**資料繫結**)。  
  
     下拉式清單控制項旁會顯示設定 欄中**資料繫結**或任何分類您已按下。  
  
8.  按一下下拉式清單，然後選取您想要查看的追蹤資訊的類型：**所有**，**重大**，**錯誤**，**警告**， **資訊**， **Verbose**，或**ActivityTracing**。  
  
     **重大**能夠追蹤 [嚴重] 事件只。  
  
     **錯誤**能夠追蹤 嚴重和錯誤事件。  
  
     **警告**可讓追蹤 嚴重、 錯誤和警告事件。  
  
     **資訊**能夠追蹤 嚴重、 錯誤、 警告和資訊事件。  
  
     **Verbose**能夠追蹤 嚴重、 錯誤、 警告、 資訊和詳細資訊的事件。  
  
     **ActivityTracing**能夠追蹤停止、 啟動、 暫停、 傳輸和繼續事件。  
  
     如需這些追蹤資訊層級含意的詳細資訊，請參閱 <xref:System.Diagnostics.SourceLevels>。  
  
9. 按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-disable-wpf-trace-information"></a>若要停用 WPF 追蹤資訊  
  
1.  在 [工具] 功能表上，選取 [選項]。  
  
2.  在**選項**對話方塊的左側方塊中開啟**偵錯**節點。  
  
3.  在下**偵錯**，按一下 [**輸出] 視窗**。  
  
4.  在右邊方塊中，尋找**WPF 追蹤設定**。  
  
5.  開啟**WPF 追蹤設定**節點。  
  
6.  在下**WPF 追蹤設定**，按一下您想要啟用的設定類別 (例如，**資料繫結**)。  
  
     下拉式清單控制項旁會顯示設定 欄中**資料繫結**或任何分類您已按下。  
  
7.  按一下下拉式清單，然後選取**關閉**。  
  
8.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 WPF](../debugger/debugging-wpf.md)