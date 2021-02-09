---
title: 在 High-Performance 叢集上進行 Debug |Microsoft Docs
description: 瞭解在高效能叢集上將多工程式偵錯工具的什麼嗎。 有兩個視窗特別有用，而且有特殊的技巧。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9703ff0e79fc4b44565b933a423a1cdcd7ff6c2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899352"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>如何：在 High-Performance 叢集上進行 Debug (c #、Visual Basic、c + +) 

在高效能叢集上偵錯多重處理程式類似在遠端電腦上偵錯一般程式。 但是，還是有一些其他的考量。 如需一般的遠端安裝需求，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

 當您在高效能叢集上偵錯時，可以使用所有可用於遠端偵錯的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯視窗和技術。 但是，因為是由遠端偵錯，所以無法使用外部主控台視窗。

 [執行緒] 和 [處理序] 視窗對偵錯平行應用程式來說特別有用。 如需如何使用這些視窗的秘訣，請參閱[How to:使用處理序視窗](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))和[逐步解說：使用執行緒視窗進行偵錯](../debugger/how-to-use-the-threads-window.md).

 下列程序顯示在高效能叢集上偵錯時特別有用的一些技術。

 當偵錯平行應用程式時，可能會想要在特定執行緒、處理序或電腦上設定中斷點。 您可以建立一般的中斷點然後加入中斷點篩選條件，以進行這項動作。

### <a name="to-open-the-breakpoint-filter-dialog-box"></a>若要開啟中斷點篩選條件對話方塊

1. 以滑鼠右鍵按一下來源視窗、[反組譯碼] 視窗、[呼叫堆疊] 視窗或 [中斷點] 視窗中的中斷點字符。

2. 在捷徑功能表上按一下 [篩選]。 這個選項可能會出現在最上層，或在 [中斷點] 的子功能表中。

### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>若要在特定電腦上設定中斷點

1. 從 [處理序] 視窗中取得電腦名稱。

2. 選取中斷點，然後根據前述程序中描述的方式開啟 [中斷點篩選] 對話方塊。

3. 在 [中斷點篩選] 對話方塊中鍵入：

     MachineName =*yourmachinename*

     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。

4. 按一下 [確定]  。

### <a name="to-set-a-breakpoint-on-a-specific-process"></a>若要在特定處理序上設定中斷點

1. 從 [處理序] 視窗中取得處理序名稱或處理序識別碼。

2. 選取中斷點，然後根據第一個程序中描述的方式開啟 [中斷點篩選] 對話方塊。

3. 在 [中斷點篩選] 對話方塊中鍵入：

       yourprocessname`ProcessName =`  

     – 或 –

      yourprocessIDnumber`ProcessID =` 

     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。

4. 按一下 [確定]  。

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>若要在特定執行緒上設定中斷點

1. 從 [執行緒] 視窗中取得執行緒名稱或執行緒識別碼。

2. 選取中斷點，然後根據第一個程序中描述的方式開啟 [中斷點篩選] 對話方塊。

3. 在 [中斷點篩選] 對話方塊中鍵入：

      yourthreadname`ThreadName =` 

     – 或 –

      yourthreadIDnumber`ThreadID =` 

     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。

4. 按一下 [確定]  。

## <a name="example"></a>範例
 下列範例顯示如何為 `marvin` 電腦和 `fourier1` 執行緒上的中斷點建立篩選條件。

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>另請參閱
- [Debug 多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [遠端偵錯](../debugger/remote-debugging.md)
- [如何：使用進程視窗](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [開始多執行緒應用程式的偵錯工具](../debugger/get-started-debugging-multithreaded-apps.md)
- [執行緒和進程](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [使用中斷點](../debugger/using-breakpoints.md)