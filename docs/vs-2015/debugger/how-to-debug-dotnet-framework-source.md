---
title: How to： Debug .NET Framework Source |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205435"
---
# <a name="how-to-debug-net-framework-source"></a>如何：偵錯 .NET Framework 原始檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

的最新版本 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供偵錯工具的新功能 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。 若要偵測 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 來源，您必須有程式碼的偵錯工具符號存取權。 您也必須啟用逐步執行 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 來源。  
  
 您可以 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 在 [ **選項** ] 對話方塊中啟用逐步執行和符號下載。 啟用符號下載時，您可以選擇立即下載符號，或是只啟用稍後下載的選項。 如果您沒有立即下載符號，便會在下次開始偵錯應用程式時下載符號。 您也可以從 [ **模組** ] 視窗或 [ **呼叫堆疊** ] 視窗手動下載。  
  
### <a name="to-enable-net-framework-source-debugging"></a>若要啟用 .NET Framework 原始檔偵錯  
  
1. 在 **[工具]** 功能表上，按一下 **[選項]** 。  
  
2. 在 [ **選項** ] 對話方塊中，按一下 [ **調試** ] 類別。  
  
3. 在 [ **一般** ] 方塊中，設定 [ **啟用 .NET Framework** 來源逐步執行]。  
  
    1. 如果您已啟用 Just My Code，將會出現警告對話方塊，通知您 Just My Code 現在已停用。 按一下 [確定]  。  
  
    2. 如果您未設定符號快取區位置，將會出現另一個對話方塊，通知您現在已經設定預設的符號快取區位置。 按一下 [確定]  。  
  
4. 在 [ **調試** ] 分類底下，按一下 [ **符號**]。  
  
5. 如果您想要變更符號快取位置：  
  
    1. 開啟左邊方塊中的 [ **調試** ] 節點。  
  
    2. 在 [ **調試** ] 節點底下，按一下 [ **符號**]。  
  
    3. 編輯快取符號中的位置 **，從符號伺服器到這個目錄** ，或按一下 **[流覽]** 選擇位置。  
  
6. 如果您想要立即下載符號，請按一下 [ **使用上述位置載入符號**]。  
  
     這個按鈕不能在設計模式中使用。  
  
     如果您沒有選擇立即下載符號，便會在下次開始偵錯程式時，自動下載符號。  
  
7. 按一下 **[確定]** 關閉 **[選項]** 對話方塊。  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>若要使用模組視窗載入 Framework 符號  
  
1. 在 [ **模組** ] 視窗中，以滑鼠右鍵按一下未載入符號的模組。 您可以藉由查看 [ **符號狀態** ] 欄來分辨是否已載入符號。  
  
2. 指向 [ **載入符號來源** ]，然後按一下 [ **microsoft 符號伺服器** ]，從 microsoft 公用符號伺服器或 **符號路徑** 下載符號，以從您先前儲存符號的目錄載入。  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>若要使用呼叫堆疊視窗載入 Framework 符號  
  
1. 在 [ **呼叫堆疊** ] 視窗中，以滑鼠右鍵按一下未載入符號的框架。 該框架隨即變成暗灰色。  
  
2. 指向 [ **載入符號來源** ]，然後按一下 [ **Microsoft 符號伺服器** ] 或 [ **符號路徑**]。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)   
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
