---
title: 如何： 偵錯.NET Framework 原始檔 |Microsoft Docs
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
ms.openlocfilehash: c06a2328987201198bc2d5d15a4788d2a821d7b6
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219116"
---
# <a name="how-to-debug-net-framework-source"></a>如何：偵錯 .NET Framework 原始檔
偵錯.NET Framework 原始檔，您必須偵錯符號的程式碼的存取權。 您也需要啟用逐步執行.NET Framework 原始檔。  
  
 您可以啟用.NET Framework 逐步執行和下載中的符號**選項** 對話方塊。 啟用符號下載時，您可以選擇立即下載符號，或是只啟用稍後下載的選項。 如果您沒有立即下載符號，便會在下次開始偵錯應用程式時下載符號。 您也可以進行手動下載從**模組** 視窗或**呼叫堆疊**視窗。  
  
### <a name="to-enable-net-framework-source-debugging"></a>若要啟用 .NET Framework 原始檔偵錯  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  在 [**選項**] 對話方塊中，按一下**偵錯**類別目錄。  
  
3.  在**一般**方塊中，設定**啟用.NET Framework 原始碼逐步偵錯。**  
  
    1.  如果您已啟用 Just My Code，將會出現警告對話方塊，通知您 Just My Code 現在已停用。 按一下 [確定 **Deploying Office Solutions**]。  
  
    2.  如果您未設定符號快取區位置，將會出現另一個對話方塊，通知您現在已經設定預設的符號快取區位置。 按一下 [確定 **Deploying Office Solutions**]。  
  
4.  底下**偵錯**分類中，按一下**符號**。  
  
5.  如果您想要變更符號快取位置中，編輯中的位置**快取此目錄中的符號**或按**瀏覽**選擇的位置。  
  
6.  如果您想要立即下載符號，請按一下**載入符號使用上述位置**。  
  
     此按鈕不是在設計模式中使用，但可在偵錯時。  
  
     如果您沒有選擇立即下載符號，便會在下次開始偵錯程式時，自動下載符號。  
  
7.  按一下 [確定] 關閉 [選項] 對話方塊。  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>若要使用模組視窗載入 Framework 符號  
  
1.  在 [**模組**] 視窗 (偵錯時，選擇**偵錯** > **Windows** > **模組**)，以滑鼠右鍵按一下未載入符號的模組。 如果已載入符號，或者不是藉由查看，您可以告訴**符號狀態**資料行。  
  
2.  指向**符號設定**然後按一下**Microsoft 符號伺服器**從 Microsoft 公用符號伺服器下載符號。 或者，您可以以滑鼠右鍵按一下模組並選擇**載入符號**從您先前儲存符號的目錄載入。  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>若要使用呼叫堆疊視窗載入 Framework 符號  
  
1.  在 [**呼叫堆疊**] 視窗中，以滑鼠右鍵按一下未載入符號的框架。 該框架隨即變成暗灰色。  
  
2.  指向**符號設定**然後按一下**Microsoft 符號伺服器**，或以滑鼠右鍵按一下模組並選擇 **符號路徑**。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)