---
title: 步驟 1：建立 Windows Forms 應用程式專案
description: 瞭解如何為您的圖片檢視器建立 Windows Forms 應用程式專案。
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76225685a9f68ca6f6cb05f902922f8fa208015d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480391"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>步驟 1：建立 Windows Forms 應用程式專案

當您建立圖片檢視器時，第一個步驟是建立 Windows Forms 應用程式專案。

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>開啟 Visual Studio 2017

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 對話方塊看起來應該類似下列螢幕擷取畫面。

     ![[新增專案] 對話方塊](../ide/media/newprojectdialogcallouts.png)<br/>**_新增專案_* _ _dialog box *

2. 在 [ **新增專案** ] 對話方塊的左側，選擇 [ **Visual c #** ] 或 [ **Visual Basic**]，然後選擇 [ **Windows 桌面**]。

3. 在 [專案範本] 清單中，選擇 [ **Windows Forms 應用程式] ( .NET Framework)**。 將新表單命名為 *PictureViewer*，然後選擇 [確定] 按鈕。

    >[!NOTE]
    >如果您未看到 [Windows Forms 應用程式 (.NET Framework)] 範本，請使用 Visual Studio 安裝程式來安裝 [.NET 桌面開發] 工作負載。<br/><br/>![Visual Studio 安裝程式中的 .NET 桌面開發工作負載](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> 如需詳細資訊，請參閱[安裝 Visual Studio](../install/install-visual-studio.md) 頁面。

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>開啟 Visual Studio 2019

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

   ![檢視 [建立新專案] 視窗](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [建立新專案] 視窗中，在搜尋方塊內輸入或鍵入 *Windows Forms*。 接下來，從 [**專案類型**] 清單中選擇 [**桌面**]。

   套用 **專案類型** 篩選準則之後，請選擇 [ **Windows Forms 應用程式] ( [.NET Framework])** 範本或 [Visual Basic]，然後選擇 **[下一步]**。

   ![選擇 Windows Forms 應用程式 ( .NET Framework 的 c # 或 Visual Basic 範本) ](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > 如果您沒有看到 [ **Windows Forms 應用程式] ( .NET Framework)** 範本，您可以從 [ **建立新專案** ] 視窗進行安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > 接下來，在 Visual Studio 安裝程式中選擇 **.NET 桌面開發** 工作負載。
   >
   > ![Visual Studio 安裝程式中的 .NET Core 工作負載](../ide/media/install-dot-net-desktop-env.png)
   >
   > 接下來，選擇 Visual Studio 安裝程式中的 [修改] 按鈕。 系統可能會提示您儲存工作，若收到提示，請依提示執行。 接下來，選擇 [繼續] 以安裝工作負載。

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 *PictureViewer*。 然後，選擇 [ **建立**]。

::: moniker-end

Visual Studio 會為您的應用程式建立解決方案。 解決方案會作為應用程式所需之所有專案和檔案的容器。 本教學課程稍後將會詳細說明這些詞彙。

## <a name="about-the-windows-forms-app-project"></a>關於 Windows Forms 應用程式專案

1. 開發環境包含三個視窗：主視窗、[方案總管] 和 [屬性] 視窗。

     如果其中有任何視窗遺失，您可以還原預設的視窗版面配置。 在功能表列上，選擇 [**視窗**  >  **重設視窗** 配置]。

     您也可以使用功能表命令顯示視窗。 在功能表列上，選擇 [**視圖**  >  **屬性視窗]** 或 [**方案總管**]。

     如果有任何其他視窗開啟，請選擇視窗右上角的 [關閉] (x) 按鈕將視窗關閉。

    ::: moniker range="vs-2017"

    * **主視窗**：您將在這個視窗中進行大部分的工作，例如，使用表單和編輯程式碼。 視窗在 [表單編輯器] 中顯示表單。 視窗頂端會出現 [起始頁] 索引標籤和 [Form1.cs [Design]] 索引標籤 (在 Visual Basic 中，索引標籤名稱的結尾是 *.vb*，而不是 *.cs*)。

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **主視窗**：您將在這個視窗中進行大部分的工作，例如，使用表單和編輯程式碼。 視窗在 [表單編輯器] 中顯示表單。

    ::: moniker-end

    * **方案總管視窗**：在這個視窗中，您可以檢視和巡覽至方案中的所有項目。

    如果您選擇一個檔案，[屬性] 視窗的內容會隨著變更。 如果您開啟程式碼檔案 (以 c # 中的 *.cs* 和 Visual Basic) 的 *.vb* 結尾，則程式碼檔案或程式碼檔的設計工具隨即出現。 設計工具是一個視覺化介面，您可以將控制項 (例如按鈕和清單) 加入該介面中。 Visual Studio 表單的設計工具稱為 **Windows Forms 設計工具**。

    * **屬性視窗**：在這個視窗中，您可以變更在其他視窗中所選擇項目的屬性。 例如，如果您選擇 Form1，可以設定 **Text** 屬性變更其標題，也可以設定 **Backcolor** 屬性變更背景色彩。

      > [!NOTE]
      > 方案總管中的第一行會顯示 [方案 'PictureViewer' (1 個專案)]，表示 Visual Studio 已為您建立方案。 方案可以包含多個專案，不過，您將暫時使用只包含一個專案的方案。

1. 在功能表列上 **，選擇 [**  >  **全部儲存**]。

     或者，選擇工具列上的 [ **全部儲存** ] 按鈕，如下圖所示。

     ![[全部儲存] 工具列按鈕](../ide/media/express_iconsaveall.png)<br/>
     **_全部儲存_* _ _toolbar 按鈕 *

     Visual Studio 會自動填入資料夾名稱和專案名稱，然後將專案儲存在專案資料夾中。

## <a name="next-steps"></a>後續步驟

* 若要移至下一個教學課程步驟，請參閱 **[步驟2：執行您的應用程式](../ide/step-2-run-your-program.md)**。

* 若要回到概觀主題，請參閱[教學課程 1：建立圖片檢視器](../ide/tutorial-1-create-a-picture-viewer.md)。

## <a name="see-also"></a>另請參閱

* [教學課程2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
