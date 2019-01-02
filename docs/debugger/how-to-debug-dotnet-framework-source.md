---
title: HOW TO：.NET Framework 原始檔進行偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a627c2f0880aee9906e3478b268d688c59b7d090
ms.sourcegitcommit: 6efb9378a82924cb133912d207c6da4bd5a0b9c2
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2018
ms.locfileid: "53443908"
---
# <a name="how-to-debug-net-framework-source"></a>HOW TO：對 .NET Framework 原始檔進行偵錯

若要偵錯.NET Framework 原始檔，您必須：

- 啟用逐步執行.NET Framework 原始檔。  
  
- 具有存取權的程式碼偵錯符號。 
  
  您可以選擇下載立即偵錯符號，或是設定稍後下載的選項。 如果您不立即下載符號，便會下載的下次您啟動偵錯您的應用程式。 偵錯時，您也可以使用**模組**或是**呼叫堆疊**windows 下載，並載入符號。  
  
### <a name="to-enable-stepping-into-net-framework-source"></a>若要啟用逐步執行.NET Framework 原始檔 
  
1. 底下**工具**(或**偵錯**) >**選項** > **偵錯** > **一般**，選取**啟用.NET Framework 原始碼逐步偵錯**。  
   
   - 如果您已啟用 Just My Code，將會出現警告對話方塊，通知您 Just My Code 現在已停用。 選取 [確定]。  
   
   - 如果您沒有本機符號快取設定，則會警告對話方塊，告訴您已設定預設的符號快取。 選取 [確定]。  
   
1. 選取  **確定**以關閉**選項**對話方塊。
  
### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>若要設定或變更符號的來源位置和載入行為

1. 選取 **符號**類別下的**工具**(或**偵錯**) >**選項** > **偵錯**.  
  
1. 在 **符號**頁面的 **符號檔 (.pdb) 位置**，選取**Microsoft 符號伺服器**從公用 Microsoft 符號伺服器的存取符號。 選取要新增其他符號位置以及變更載入順序的工具列按鈕。 
   
1. 若要變更您的本機符號快取，編輯，或瀏覽至不同的位置底下**快取此目錄中的符號**。  
   
1. 若要立即下載符號，選取**載入所有符號**。 偵錯時，這個按鈕才有效。  
   
   如果您不立即下載符號，它們會下載的下次您啟動偵錯。  
   
1. 選取  **確定**以關閉**選項**對話方塊。  
  
### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>若要載入符號的模組或呼叫堆疊視窗  
  
1. 偵錯時，請選取，視窗中開啟**偵錯** > **Windows** > **模組**(或按**Ctrl + Alt + U**)或是**偵錯** > **Windows** > **呼叫堆疊**(**Ctrl + Alt + C**)。 
   
1. 以滑鼠右鍵按一下未載入符號的模組。 在 [**模組**] 視窗中，符號載入作業的狀態處於**符號狀態**資料行。 在 [**呼叫堆疊**] 視窗中，狀態不**框架狀態**資料行，並在畫面格是灰色。 
   
   - 選取 [**載入符號**] 功能表尋找並載入符號檔從您的電腦上的資料夾中。 
   
   - 選取 **符號載入資訊**顯示偵錯工具搜尋符號的位置。  
   
   - 選取 **符號設定**來開啟**符號**頁面。 在 **符號**頁面的 **符號檔 (.pdb) 位置**，選取**Microsoft 符號伺服器**從公用 Microsoft 符號伺服器的存取符號。 選取要新增其他符號位置以及變更載入順序的工具列按鈕。 選取 **確定**以關閉對話方塊。 
  
### <a name="see-also"></a>另請參閱  
 [針對受控碼進行偵錯](../debugger/debugging-managed-code.md)   
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)