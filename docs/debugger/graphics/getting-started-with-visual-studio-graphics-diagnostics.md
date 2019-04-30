---
title: 開始使用圖形診斷 |Microsoft Docs
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fc7dd207a525eaed12db1b2e45e7720d96ee8b6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388704"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷快速入門
在本節中，您將準備第一次使用圖形診斷，並從 Direct3D 應用程式擷取畫面格，然後在圖形分析器中檢查它們。

## <a name="requirements"></a>需求
 若要在 Visual Studio 中使用圖形診斷，您必須使用 Visual Studio Enterprise、 Visual Studio Professional 或 Visual Studio Community。  其他版本，包括 Visual Studio Code 中，並包含這項功能。

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 必要條件
 選擇性 Windows 功能「圖形工具」提供 Windows 10 上圖形診斷所需的擷取和播放基礎結構。

 如需安裝圖形工具的相關資訊，請參閱[安裝適用於 Windows 10 的圖形工具](#InstallGraphicsTools)。

## <a name="InstallGraphicsTools"></a> 安裝適用於 Windows 10 的圖形工具
 在 Windows 10 中，圖形診斷基礎結構是由稱為「圖形工具」的選擇性 Windows 功能所提供。 不論所擷取應用程式的目標設為舊版 Windows 還是它所使用的 Direct3D 版本，都需要有這項功能，才能在 Windows 10 上擷取和播放圖形資訊。 您可以選擇事先安裝圖形工具功能；否則它會在第一次從 Visual Studio 啟動圖形診斷工作階段時視需要安裝。

#### <a name="to-install-graphics-tools-for-windows-10"></a>安裝適用於 Windows 10 的圖形工具

1. 在搜尋中，輸入**應用程式和功能**，然後開啟**應用程式與功能**設定。

2. 右手邊**應用程式與功能** 對話方塊中，選擇**管理選擇性功能**(在**應用程式與功能**)。

   [管理選擇性功能] 對話方塊隨即出現。

3. 在 [管理選擇性功能] 對話方塊中，選擇 [新增功能]。 您可以安裝的選擇性功能清單隨即出現。

4. 從功能清單中選取 [圖形工具]，然後選擇 [安裝]。

   安裝 Windows SDK 時，也會自動安裝圖形工具功能。

> [!TIP]
> Windows 10 的選擇性圖形工具功能提供輕量型擷取和播放功能 (例如命令列擷取程式 **dxcap.exe**)，以用於未安裝開發人員工具之電腦的支援、測試和診斷案例。 如需詳細資訊，請參閱[命令列擷取工具](command-line-capture-tool.md)主題。

## <a name="using-graphics-diagnostics-for-the-first-time"></a>第一次使用圖形診斷
 您現在已具備所有必要元件，可以開始使用圖形診斷。 請依照下列步驟進行。

### <a name="1---create-a-direct3d-app"></a>1 - 建立 Direct3D 應用程式
 如果您已經有自己的 Direct3D 應用程式，來瀏覽圖形診斷，太好了 ！ 否則，請使用下列其中一項：

- **DirectX 11 應用程式 (通用 Windows)** 或是**DirectX 12 應用程式 (通用 Windows)** 適用於 Windows 10 的專案範本。
- [Direct3D 12 UAP 範例](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f)適用於 Windows 10。

  繼續前請先確定您可以建置應用程式。

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - 啟動圖形診斷工作階段
 您現在已經準備好開始第一個圖形診斷工作階段。 在 Visual Studio 主功能表上，選擇**偵錯，圖形開始圖形偵錯**，或直接按**alt+f5**。 這樣會使用圖形診斷來啟動您的應用程式，並在 Visual Studio 中顯示診斷工作階段視窗。

> [!IMPORTANT]
> 如果您是在 Windows 10 上執行應用程式，並且尚未安裝選擇性圖形工具功能，則系統會提示您現在這麼做。 您必須先安裝它，才能在 Windows 10 上使用圖形診斷。

### <a name="3---capture-frames"></a>3 - 擷取畫面格
 只要您啟動應用程式，就已準備好擷取畫面格。

#### <a name="to-capture-single-frames"></a>擷取單一畫面格

- 在 Visual Studio 中，選擇 [圖形] 工具列或診斷工作階段視窗中的 [擷取畫面格] 按鈕。 或者，如果您的應用程式具有焦點，請按**Print Screen**鍵盤上。

#### <a name="to-capture-a-sequence-of-frames"></a>擷取一系列畫面格

- 在 Visual Studio 中，將診斷工作階段視窗中的 [要擷取的畫面格] 設為您要依序擷取的畫面格數目，然後使用您在上面描述的任何方法擷取單一畫面格以擷取該序列。

   若要再次擷取單一畫面格，請將 [要擷取的畫面格] 設為 *1*。

  完成畫面格的擷取時，只要結束應用程式，或選擇 [圖形] 工具列或診斷工作階段視窗中的 [停止] 按鈕。

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - 在 [圖形分析器] 中檢查擷取的畫面格
 您現在可以檢查剛剛擷取的畫面格。 若要開始分析畫面格，請從診斷工作階段視窗中選擇您要檢查之畫面格的畫面格編號。 這會在 [圖形分析器] 中開啟畫面格，您可以在其中使用圖形診斷工具來檢查您的應用程式如何使用 Direct3D 來追蹤轉譯問題，或使用 [畫面格分析] 工具來了解其效能。

 如果您已從診斷工作階段視窗中選取錯誤的畫面格，或想要檢查不同的畫面格，則可以從圖形分析器中選取新的畫面格。 在圖形記錄視窗的 [轉譯目標] 索引標籤中，展開轉譯目標影像下的 [畫面格清單]，然後選擇不同的畫面格進行檢查。

 若要深入了解如何搭配使用圖形分析器工具，請參閱[範例](graphics-diagnostics-examples.md)。

## <a name="see-also"></a>另請參閱
- [Direct3D 12 圖形](/windows/desktop/direct3d12/direct3d-12-graphics)