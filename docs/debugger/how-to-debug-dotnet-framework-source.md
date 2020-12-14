---
title: Debug .NET Framework source |Microsoft Docs
Description: 瞭解如何 .NET Framework 來源進行調試。 您必須為其設定，並下載偵錯工具符號。
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 13a575ec2e77f1b715ec5f17324a6933d8cf0805
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398619"
---
# <a name="how-to-debug-net-framework-source"></a>How to: Debug .NET Framework source (如何：對 .NET Framework 來源進行偵錯)

若要 .NET Framework 來源進行 debug 錯，您必須：

- 啟用逐步執行 .NET Framework 來源。

- 可以存取程式碼的偵錯工具符號。

  您可以選擇立即下載偵錯工具符號，或設定選項以供稍後下載。 如果您沒有立即下載符號，則會在您下次開始將應用程式進行偵錯工具時下載。 在進行調試時，您也可以使用 **模組** 或 **呼叫堆疊** 視窗來下載和載入符號。

### <a name="to-enable-stepping-into-net-framework-source"></a>若要啟用逐步執行 .NET Framework 來源

1. 在 [**工具**] (或 [ **Debug** ]) >**選項**  >    >  的 **[一般**] 調試，選取 [**啟用 .NET Framework 來源逐步執行**]

   - 如果您已啟用 Just My Code，將會出現警告對話方塊，通知您 Just My Code 現在已停用。 選取 [確定]。

   - 如果您沒有本機符號快取集，則會出現警告對話方塊，告訴您已設定預設的符號快取。 選取 [確定]。

1. 選取 **[確定** ] 以關閉 [ **選項** ] 對話方塊。

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>若要設定或變更符號來源位置和載入行為

1. 在 [**工具** (] 或 [ **Debug** ]) >**選項**] 下選取 [**符號**] 類別  >  ****。

1. 在 [ **符號** ] 頁面的 [ **符號檔 ( .pdb) 位置**] 底下，選取 [ **Microsoft 符號伺服器** ] 以存取公用 Microsoft 符號伺服器的符號。 選取工具列按鈕以新增其他符號位置，並變更載入順序。

1. 若要變更您的本機符號快取，請 **在此目錄中** 的 [快取符號] 下編輯或流覽至不同的位置。

1. 若要立即下載符號，請選取 [ **載入所有符號**]。 只有在進行偵錯工具時，才能使用此按鈕。

   如果您沒有立即下載符號，則會在您下次開始進行調試時下載。

1. 選取 **[確定** ] 以關閉 [ **選項** ] 對話方塊。

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>從模組或呼叫堆疊視窗載入符號

1. 在偵錯工具期間，藉由選取 [ **Debug**  >  **Windows**  >  **模組**] (，或按 **ctrl + alt + U**) 或 [   >    >   (**ctrl + alt + C**) 的偵錯工具] 來開啟視窗。

1. 以滑鼠右鍵按一下未載入符號的模組。 在 [ **模組** ] 視窗中，符號載入狀態是在 [ **符號狀態** ] 欄中。 在 [ **呼叫堆疊** ] 視窗中，[狀態] 是在 [ **框架狀態** ] 資料行中，而框架則呈現灰色。

   - 選取功能表中的 [ **載入符號** ]，即可從您電腦上的資料夾找出並載入符號檔。

   - 選取 [ **符號載入資訊** ]，以顯示偵錯工具搜尋符號的位置。

   - 選取 [ **符號設定** ] 以開啟 [ **符號** ] 頁面。 在 [ **符號** ] 頁面的 [ **符號檔 ( .pdb) 位置**] 底下，選取 [ **Microsoft 符號伺服器** ] 以存取公用 Microsoft 符號伺服器的符號。 選取工具列按鈕以新增其他符號位置，並變更載入順序。 選取 **[確定** ] 以關閉對話方塊。

### <a name="see-also"></a>另請參閱
- [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)
- [指定符號 ( .pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)