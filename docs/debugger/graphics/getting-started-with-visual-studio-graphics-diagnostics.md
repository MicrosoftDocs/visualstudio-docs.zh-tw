---
title: "開始使用 Visual Studio 圖形診斷 |Microsoft 文件"
ms.custom: 
ms.date: 05/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 577fd16d93bdfd1ad15bb3469495fdd1342a6994
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷快速入門
在本節中，您將準備第一次使用圖形診斷，並從 Direct3D 應用程式擷取畫面格，然後在圖形分析器中檢查它們。  
  
## <a name="requirements"></a>需求  
 若要在 Visual Studio 中使用圖形診斷，您必須使用 Visual Studio Enterprise、 Visual Studio Professional 或 Visual Studio Community。  其他版本，包括 Visual Studio 程式碼，並包含這項功能。
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Windows 10 必要條件  
 選擇性 Windows 功能*圖形工具*提供 Windows 10 上圖形診斷所需的擷取和播放基礎結構。  
  
 如需安裝圖形工具的詳細資訊，請參閱[安裝圖形工具適用於 Windows 10](#InstallGraphicsTools)。  
  
### <a name="windows-81-prerequisites"></a>Windows 8.1 必要條件  
 適用於 Windows 8.1 的 Windows 軟體開發套件 (SDK) 提供 Windows 8.1 上圖形診斷所需的擷取和播放基礎結構，並且支援 Windows 8.1 和 Windows 8 的開發。  
  
 [下載 Windows 8.1 的 Windows 軟體開發套件 (SDK)](https://msdn.microsoft.com/en-us/windows/desktop/bg162891.aspx)  
  
 若要從執行 Windows 8.1 的開發電腦使用執行 Windows 10 的遠端播放電腦，您必須在開發電腦上安裝 Windows 10 SDK，並在播放電腦上安裝選擇性圖形工具功能。  
  
##  <a name="InstallGraphicsTools"></a>安裝適用於 Windows 10 的圖形工具  
 在 Windows 10 中，圖形診斷基礎結構由稱為 Windows 的選用功能*圖形工具*。 不論所擷取應用程式的目標設為舊版 Windows 還是它所使用的 Direct3D 版本，都需要有這項功能，才能在 Windows 10 上擷取和播放圖形資訊。 您可以選擇事先安裝圖形工具功能；否則它會在第一次從 Visual Studio 啟動圖形診斷工作階段時視需要安裝。  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>安裝適用於 Windows 10 的圖形工具  
  
1.  在搜尋中，輸入**應用程式和功能**，然後開啟**應用程式和功能**設定。
  
3.  右側的**應用程式和功能** 對話方塊中，選擇**管理選擇性功能**(下**應用程式和功能**)。

    **管理選擇性功能**對話方塊隨即出現。
  
4.  在**管理選擇性功能** 對話方塊中，選擇**將功能加入**。 您可以安裝的選擇性功能清單隨即出現。  
  
5.  選取**圖形工具**從功能清單，然後選擇 **安裝**。  
  
 安裝 Windows 10 SDK 時，也會自動安裝圖形工具功能。  
  
> [!TIP]
>  Windows 10 的選擇性圖形工具功能提供輕量型擷取和播放功能，例如命令列擷取程式**dxcap.exe**—，可以用支援、 測試和診斷案例未安裝開發人員工具的機器。 如需詳細資訊，請參閱[命令列擷取工具](command-line-capture-tool.md)主題。  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>第一次使用圖形診斷  
 您現在已具備所有必要元件，可以開始使用圖形診斷。 請依照下列步驟進行。  
  
### <a name="1---create-a-direct3d-app"></a>1 - 建立 Direct3D 應用程式  
 如果您已經有專屬 Direct3D 應用程式來瀏覽圖形診斷，很好 ！ 否則，請使用下列其中一項：

- **DirectX 11 應用程式 (通用 Windows)**或**DirectX 12 應用程式 (通用 Windows)** for Windows 10 專案範本。
- **DirectX 應用程式 (Windows 8.1)**用於 Windows 8.1 專案範本。
- [Direct3D 12 UAP 範例](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f)for Windows 10。  
- [DirectX 彈珠迷宮遊戲範例](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)針對 Windows 8.1。  
  
 繼續前請先確定您可以建置應用程式。  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 - 啟動圖形診斷工作階段  
 您現在已經準備好開始第一個圖形診斷工作階段。 在 Visual Studio 主功能表上，選擇**偵錯，圖形中，啟動圖形偵錯**，或直接按**Alt + F5**。 這樣會使用圖形診斷來啟動您的應用程式，並在 Visual Studio 中顯示診斷工作階段視窗。  
  
> [!IMPORTANT]
>  如果您是在 Windows 10 上執行應用程式，並且尚未安裝選擇性圖形工具功能，則系統會提示您現在這麼做。 您必須先安裝它，才能在 Windows 10 上使用圖形診斷。  
  
### <a name="3---capture-frames"></a>3 - 擷取畫面格  
 只要您啟動應用程式，就已準備好擷取畫面格。  
  
#### <a name="to-capture-single-frames"></a>擷取單一畫面格  
  
-   在 Visual Studio 中，選擇 **擷取框架**按鈕，從 圖形 工具列或診斷工作階段視窗。 或者，如果您的應用程式具有焦點，請按**Print Screen**鍵盤上的索引鍵。
  
#### <a name="to-capture-a-sequence-of-frames"></a>擷取一系列畫面格  
  
-   在 Visual Studio 中，在診斷工作階段 視窗中，設定**框架以取得**至您想要在順序中擷取的畫面格數目，然後擷取順序 」 使用任何您要擷取單一畫面格上述的方法。  
  
     若要再次擷取單一畫面格，將**框架以取得**至*1*。  
  
 當您完成時擷取的畫面格只要結束應用程式，或選擇**停止**按鈕，從 [圖形] 工具列或診斷工作階段視窗。  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4-檢查在圖形分析器中擷取的畫面格  
 您現在可以檢查剛剛擷取的畫面格。 若要開始分析畫面格，請從診斷工作階段視窗中選擇您要檢查之畫面格的畫面格編號。 這會開啟中的框架**圖形分析器**，其中您可以使用圖形診斷工具來檢查您的應用程式如何使用 Direct3D 來追蹤轉譯問題，或使用**畫面格分析**工具了解其效能。  
  
 如果您已從診斷工作階段視窗中選取錯誤的畫面格，或想要檢查不同的畫面格，則可以從圖形分析器中選取新的畫面格。 在**轉譯目標** 索引標籤的圖形記錄視窗中，在轉譯目標影像中，展開**畫面格清單**，然後選擇不同的畫面格進行檢查。  
  
 若要深入了解如何搭配使用圖形分析器工具，請參閱[範例](graphics-diagnostics-examples.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Direct3D 12 的圖形](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)