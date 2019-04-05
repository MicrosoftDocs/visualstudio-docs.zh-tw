---
title: HOW TO：使用 Code Center Premium 來源進行偵錯 |Microsoft Docs
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
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0290fa7c83b36c19663aef85c0179fb9458ddcf
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "59000786"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>HOW TO：使用 Code Center Premium 來源進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

利用 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 偵錯工具，您可以從 Microsoft MSDN Code Center Premium 對安全共用來源進行偵錯。  
  
 本主題說明在 Visual Studio 中，安裝和偵錯 Code Center Premium 原始程式碼的方法。  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>若要準備使用 Code Center Premium 進行偵錯  
  
1. 連接智慧卡讀取裝置，並插入您從共享原始碼計畫取得的卡片。  
  
2. 啟動 Visual Studio。  
  
3. 在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
4. 在 **選項**對話方塊中，開啟**偵錯**節點，然後按一下**一般**。  
  
5. 清除**啟用 Just My Code （僅限 Managed）** 核取方塊。  
  
6. 選取 **啟用來源伺服器支援**。  
  
7. 清除**需要來源檔案以完全符合原始版本**。  
  
8. 底下**偵錯**節點中，按一下**符號**。  
  
9. 在 **符號檔 (.pdb) 位置**方塊中，清除**Microsoft 伺服器符號**核取方塊，然後加入下列位置：  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  請務必包含結尾斜線<strong>/</strong> 路徑的結尾。  
  
     將這些位置移至清單頂端，以確保優先載入這些符號。  
  
   > [!NOTE]
   >  這些 Code Center Premium 位置必須先列出，才能讓它們成為優先載入的位置。 在 Visual Studio 2010 中，您無法將上述任何伺服器移**Microsoft 符號伺服器**項目，這就是為什麼您必須清除此核取方塊。  
   > 
   >  若要在偵錯工作階段期間從 Microsoft 符號載入符號，請執行下列作業：  
   > 
   > 1. 在 **偵錯**功能表上，選擇**Windows** ，然後選擇**模組**。  
   >    2.  選取想要其符號的模組，然後開啟捷徑功能表。 選擇**載入符號來源**，然後選擇**Microsoft 符號伺服器**。  
  
10. 在 **快取從符號伺服器，此目錄中的符號**方塊中，輸入位置，例如`C:\symbols`Code Center Premium 可以快取符號。 將符號進行快取可大幅提升偵錯期間的效能。  
  
     如果在完成此程序之後，您無法使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 來偵錯原始程式碼，請檢查快取位置中是否有先前已快取且過期的符號檔。 移除過期的符號檔。  
  
11. 按一下 [確定 **Deploying Office Solutions**]。  
  
12. 重新啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 以確實保存設定。  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>若要使用附加至處理序來偵錯原始程式碼  
  
1.  連接智慧卡讀取裝置，並插入您從共享原始碼計畫取得的卡片。  
  
2.  啟動 Visual Studio。  
  
3.  開啟您的 Visual Studio 專案。  
  
4.  在 **工具**功能表上，按一下**附加至處理序**。  
  
5.  在 [ **připojit k procesu** ] 對話方塊中，按一下**選取**。  
  
6.  在 **選取程式碼類型**對話方塊的 **偵測這些程式碼類型**，選取**原生**，**受控**，和**管理 （v4.0)**。  
  
7.  按一下 [ **[確定]** 以關閉**選取程式碼類型**] 對話方塊。  
  
8.  在 **可用的處理序**方塊中，選取您想要偵錯的處理序。  
  
9. 按一下 [附加] 。  
  
10. 當系統提示您確認您的憑證時，按一下**確定**。 然後輸入您的 PIN。 接受 Code Center Premium 使用條款 (如果系統提示您接受的話)。  
  
     依網路速度而定，下載符號可能需要許多時間。 當所有符號都已順利下載時，狀態列會顯示相關文字。  
  
11. 針對方案中的所有 Managed 專案，重複執行附加步驟。  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>若要從現有的方案偵錯原始程式碼  
  
1. 在 **方案總管**，開啟方案的捷徑功能表，然後選擇**屬性**。  
  
2. 在 [方案屬性頁] 對話方塊中，選擇**偵錯原始程式檔**中**通用屬性**節點。  
  
3. 新增下列位置，即可**包含原始程式檔的目錄**清單：  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  請務必包含結尾斜線<strong>/</strong> 路徑的結尾。  
  
4. 針對方案中的每個 Managed 專案執行下列作業  
  
   1.  在 [方案總管] 中，開啟專案的捷徑功能表，然後再選擇**屬性**。  
  
   2.  選取 **偵錯**，然後選擇**啟用 unmanaged 程式碼偵錯**。  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>若要偵錯使用 Code Center Premium 來源的方案  
  
1.  在 `Package` 類別中，在 package 建構函式設定中斷點。  
  
2.  在 `Debug`功能表上，按一下**啟動偵錯**。  
  
3.  當您叫用在 package 建構函式中斷點時，請移至**呼叫堆疊**視窗，並以滑鼠右鍵按一下您想要載入的組件的堆疊框架的符號，然後按一下**載入符號**。  
  
     按兩下呼叫堆疊以載入原始檔。  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>若要瀏覽 Code Center Premium 上的原始程式碼  
  
1.  連接智慧卡讀取裝置，並插入您從共享原始碼計畫取得的卡片。  
  
2.  啟動 Internet Explorer，輸入下列 URL：`https://codepremium.msdn.microsoft.com`  
  
3.  瀏覽並尋找您想要的原始檔。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
