---
title: 只是時間，偵錯、 選項對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5522c9da025b76a3892d3923cdd7397b8ed5ce5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207489"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>選項對話方塊、偵錯、Just-In-Time
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要存取**Just In Time**頁面上，移至**工具**功能表，然後按一下**選項**。 在 **選項**對話方塊方塊中，展開**偵錯**節點，然後選取**Just In Time**。 這個頁面可讓您啟用 Managed 程式碼、機器碼和指令碼的 Just-In-Time 偵錯。 如需詳細資訊，請參閱 < [Just-In-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)。  
  
 您可以為這些程式類型啟用 Just-In-Time 偵錯：  
  
-   Managed  
  
-   原生  
  
-   指令碼  
  
 Just-In-Time 偵錯一項技術，可讓您對 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 外部啟動的程式進行偵錯。 您可以執行在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境外的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中所建立的程式。 如果您已啟用 Just-In-Time 偵錯，發生損毀時將會顯示對話方塊，詢問您是否要進行偵錯。  
  
## <a name="associated-warnings"></a>相關聯的警告  
 當您瀏覽此頁面**選項** 對話方塊中，您可能會看到一則警告訊息就像這樣：  
  
 **另一個偵錯工具已經將本身註冊的時間只需為偵錯工具。若要修復，啟用 恰好時間偵錯或執行 Visual Studio 修復。**  
  
 如果您將另一個偵錯工具設為 Just-In-Time 偵錯工具 (可能是舊版的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯工具)，就會出現這則訊息。  
  
 以下是您可能會看到的另一則訊息：  
  
 **在 Just-in-time 偵錯註冊錯誤偵測到。若要修復，啟用 恰好時間偵錯或執行 Visual Studio 修復。**  
  
 如果您看到這些警告，只要時間使用偵錯[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]需要系統管理員權限，直到您修正問題。 如果您嘗試在這些狀況下以非系統管理員身分啟用，將會看見下列錯誤訊息：  
  
 **存取遭到拒絕。系統管理員啟用 Just In Time 偵錯 」，或修復 Visual Studio 的安裝。**  
  
## <a name="see-also"></a>另請參閱  
 [選項對話方塊、 偵錯](../debugger/debugging-options-dialog-box.md)   
 [如何：指定偵錯工具設定](../debugger/how-to-specify-debugger-settings.md)



