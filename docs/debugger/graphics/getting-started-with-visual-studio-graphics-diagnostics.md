---
title: 開始使用圖形診斷 |Microsoft Docs
description: 準備第一次使用圖形診斷，然後從 Direct3D 應用程式中取得畫面格，並在 [圖形分析器] 中檢查。
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70512b4df3be7f11973af244c336b22c59c90f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387602"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷快速入門
在本節中，您將準備第一次使用圖形診斷，並從 Direct3D 應用程式擷取畫面格，然後在圖形分析器中檢查它們。

## <a name="requirements"></a>規格需求
 若要在 Visual Studio 中使用圖形診斷，您必須使用 Visual Studio Enterprise、Visual Studio Professional 或 Visual Studio Community。  其他版本，包括 Visual Studio Code，則不包含這項功能。

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 先決條件
 選擇性 Windows 功能「圖形工具」提供 Windows 10 上圖形診斷所需的擷取和播放基礎結構。

 如需安裝圖形工具的相關資訊，請參閱[安裝適用於 Windows 10 的圖形工具](#InstallGraphicsTools)。

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> 安裝適用於 Windows 10 的圖形工具
 在 Windows 10 中，圖形診斷基礎結構是由稱為「圖形工具」的選擇性 Windows 功能所提供。 不論所擷取應用程式的目標設為舊版 Windows 還是它所使用的 Direct3D 版本，都需要有這項功能，才能在 Windows 10 上擷取和播放圖形資訊。 您可以選擇事先安裝圖形工具功能；否則它會在第一次從 Visual Studio 啟動圖形診斷工作階段時視需要安裝。

#### <a name="to-install-graphics-tools-for-windows-10"></a>安裝適用於 Windows 10 的圖形工具

1. 在 [搜尋] 中，輸入 **應用程式和功能** ，然後開啟 **應用程式 & 功能** 設定。

2. 在 [應用程式的右側] **& 功能**] 設定中，選擇 [**應用程式 & 功能**] 下的 [**選用功能** (]) 。

   [ **選用功能** ] 設定隨即出現。

3. 在 [ **選用功能** 設定] 中，選擇 [ **新增功能**]。 您可以安裝的選擇性功能清單隨即出現。

4. 從功能清單中選取 [圖形工具]，然後選擇 [安裝]。

   安裝 Windows SDK 時，也會自動安裝圖形工具功能。

> [!TIP]
> Windows 10 的選擇性圖形工具功能提供輕量型擷取和播放功能 (例如命令列擷取程式 **dxcap.exe**)，以用於未安裝開發人員工具之電腦的支援、測試和診斷案例。 如需詳細資訊，請參閱[命令列擷取工具](command-line-capture-tool.md)主題。

## <a name="using-graphics-diagnostics-for-the-first-time"></a>第一次使用圖形診斷
 您現在已具備所有必要元件，可以開始使用圖形診斷。 請直接遵循下列步驟。

### <a name="1---create-a-direct3d-app"></a>1 - 建立 Direct3D 應用程式

如果您已經有自己的 Direct3D 應用程式可探索圖形診斷，很棒！ 否則，請使用下列其中一項：

::: moniker range=">=vs-2019"
從 [Direct3D 遊戲範例](/samples/microsoft/windows-universal-samples/simple3dgamedx/)下載範例。
::: moniker-end
::: moniker range="vs-2017"
- **Directx 11 應用程式 (通用 windows)** 或 **Directx 12 應用程式 (** 適用于 Windows 10 的通用 windows) 專案範本。
- Windows 10 的[Direct3D 12 UAP 範例](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f)。
::: moniker-end

請先確定您可以建立並執行應用程式，再繼續進行操作。 選擇 [**組建**  >  **組建方案**]，以確定其建立時不會發生錯誤。 然後選擇 [ **Debug**  >  **啟動但不進行調試**] (**Ctrl + F5**) ，以確定它會正確執行。 視您使用此工具測試的電腦而定，您可能需要調整範例的平臺和偵錯工具目標。 例如，若要針對 Visual Studio 主機電腦上的 x64 平臺進行測試，請選擇 [ **x64** ] 作為 [方案平臺] 和 [ **本機電腦** ] 做為您的偵錯工具目標。 

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - 啟動圖形診斷工作階段
 您現在已經準備好開始第一個圖形診斷工作階段。 在 Visual Studio 的主功能表上，選擇 [ **Debug]、[圖形]、[開始圖形調試**]，或直接按下 **Alt + F5**。 這樣會使用圖形診斷來啟動您的應用程式，並在 Visual Studio 中顯示診斷工作階段視窗。

> [!IMPORTANT]
> 如果您是在 Windows 10 上執行應用程式，並且尚未安裝選擇性圖形工具功能，則系統會提示您現在這麼做。 您必須先安裝它，才能在 Windows 10 上使用圖形診斷。

### <a name="3---capture-frames"></a>3 - 擷取畫面格
 只要您啟動應用程式，就已準備好擷取畫面格。

#### <a name="to-capture-single-frames"></a>擷取單一畫面格

- 在 Visual Studio 中，選擇 [圖形] 工具列或診斷工作階段視窗中的 [擷取畫面格] 按鈕。 或者，如果您的應用程式具有焦點，只要在鍵盤上按下 **Print Screen** 鍵即可。

#### <a name="to-capture-a-sequence-of-frames"></a>擷取一系列畫面格

- 在 Visual Studio 中，將診斷工作階段視窗中的 [要擷取的畫面格] 設為您要依序擷取的畫面格數目，然後使用您在上面描述的任何方法擷取單一畫面格以擷取該序列。

   若要再次擷取單一畫面格，請將 [要擷取的畫面格] 設為 *1*。

  完成畫面格的擷取時，只要結束應用程式，或選擇 [圖形] 工具列或診斷工作階段視窗中的 [停止] 按鈕。

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - 在 [圖形分析器] 中檢查擷取的畫面格
 您現在可以檢查剛剛擷取的畫面格。 若要開始分析畫面格，請從診斷工作階段視窗中選擇您要檢查之畫面格的畫面格編號。 這會在 [圖形分析器] 中開啟畫面格，您可以在其中使用圖形診斷工具來檢查您的應用程式如何使用 Direct3D 來追蹤轉譯問題，或使用 [畫面格分析] 工具來了解其效能。

 如果您已從診斷工作階段視窗中選取錯誤的畫面格，或想要檢查不同的畫面格，則可以從圖形分析器中選取新的畫面格。 在圖形記錄視窗的 [轉譯目標] 索引標籤中，展開轉譯目標影像下的 [畫面格清單]，然後選擇不同的畫面格進行檢查。

 若要深入瞭解如何搭配使用圖形分析器工具，請參閱 [範例](graphics-diagnostics-examples.md)。

## <a name="see-also"></a>另請參閱
- [Direct3D 12 圖形](/windows/desktop/direct3d12/direct3d-12-graphics)