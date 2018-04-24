---
title: 如何： 偵錯.NET Framework 來源 |Microsoft 文件
ms.custom: ''
ms.date: 02/23/2018
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
ms.openlocfilehash: 8377ed73479441272b2f1910767fa7e2a4ff0196
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-net-framework-source"></a>如何：偵錯 .NET Framework 原始檔
若要偵錯.NET Framework 原始程式碼，您必須偵錯符號的程式碼存取權。 您也需要啟用逐步執行.NET Framework 原始程式碼。  
  
 您可以啟用.NET Framework 逐步執行和符號中下載**選項** 對話方塊。 啟用符號下載時，您可以選擇立即下載符號，或是只啟用稍後下載的選項。 如果您沒有立即下載符號，便會在下次開始偵錯應用程式時下載符號。 您也可以進行手動下載從**模組**視窗或**呼叫堆疊**視窗。  
  
### <a name="to-enable-net-framework-source-debugging"></a>若要啟用 .NET Framework 原始檔偵錯  
  
1.  在**工具**功能表上，按一下 **選項**s。  
  
2.  在**選項**對話方塊中，按一下 **偵錯**類別目錄。  
  
3.  在**一般**方塊中，設定**啟用.NET Framework 原始碼逐步偵錯。**  
  
    1.  如果您已啟用 Just My Code，將會出現警告對話方塊，通知您 Just My Code 現在已停用。 按一下 [確定 **Deploying Office Solutions**]。  
  
    2.  如果您未設定符號快取區位置，將會出現另一個對話方塊，通知您現在已經設定預設的符號快取區位置。 按一下 [確定 **Deploying Office Solutions**]。  
  
4.  在下**偵錯**分類中，按一下 **符號**。  
  
5.  如果您想要變更符號快取位置中，編輯中的位置**快取此目錄中的符號**或按一下**瀏覽**選擇的位置。  
  
6.  如果您想要立即下載符號，請按一下**載入符號使用上述位置**。  
  
     這個按鈕不提供在設計模式中，但使用偵錯時。  
  
     如果您沒有選擇立即下載符號，便會在下次開始偵錯程式時，自動下載符號。  
  
7.  按一下 [確定] 關閉 [選項] 對話方塊。  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>若要使用模組視窗載入 Framework 符號  
  
1.  在**模組**視窗 (偵錯時，選擇 **偵錯** > **Windows** > **模組**)，以滑鼠右鍵按一下未載入符號的模組。 您可以告訴符號是否已載入，或透過查看**符號狀態**資料行。  
  
2.  指向**符號設定**按一下**Microsoft 符號伺服器**從 Microsoft 公用符號伺服器下載符號。 或者，您可以在模組上按一下滑鼠右鍵並選擇**載入符號**載入先前儲存符號的目錄。  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>若要使用呼叫堆疊視窗載入 Framework 符號  
  
1.  在**呼叫堆疊** 視窗中，以滑鼠右鍵按一下未載入符號的框架的。 該框架隨即變成暗灰色。  
  
2.  指向**符號設定**按一下**Microsoft 符號伺服器**，或以滑鼠右鍵按一下該模組，並選擇 **符號路徑**。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)