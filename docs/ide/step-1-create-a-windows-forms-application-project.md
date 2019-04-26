---
title: 步驟 1：建立 Windows Forms 應用程式專案
ms.date: 03/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f529d737816406b3a4f6aa9921a8dc6b902d2fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979850"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>步驟 1：建立 Windows Forms 應用程式專案

建立圖片檢視器的第一個步驟是建立 Windows Forms 應用程式專案。

 > [!TIP]
 > ![影片連結](../data-tools/media/playvideo.gif)如需本主題的影片版本，請參閱[教學課程 1：在 Visual Basic 中建立圖片檢視器 - 影片 1](http://go.microsoft.com/fwlink/?LinkId=205209) 或[教學課程 1：在 C# 中建立圖片檢視器 - 影片 1](http://go.microsoft.com/fwlink/?LinkId=205199)。 這些影片使用舊版 Visual Studio，因此有一些功能表命令以及某些使用者介面項目會有些微差異。 不過，概念和程序在目前 Visual Studio 版本中的運作方式雷同。

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>開啟 Visual Studio 2017

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。 對話方塊看起來會像這樣。

     ![[新增專案] 對話方塊](../ide/media/newprojectdialogcallouts.png)<br/>
[新增專案] 對話方塊

2. 在 [新增專案] 對話方塊左側，選擇 [Visual C#] 或 [Visual Basic]。

3. 在範本清單中，選擇 [Windows Forms 應用程式 (.NET Framework)]。 將新表單命名為 **PictureViewer**，然後選擇 [確定] 按鈕。

    >[!NOTE]
    >如果您未看到 [Windows Forms 應用程式 (.NET Framework)] 範本，請使用 Visual Studio 安裝程式來安裝 [.NET 桌面開發] 工作負載。<br/><br/>![Visual Studio 安裝程式中的 .NET 桌面開發工作負載](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> 如需詳細資訊，請參閱[安裝 Visual Studio](../install/install-visual-studio.md) 頁面。

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>開啟 Visual Studio 2019

1. 在開始視窗中，選擇 [建立新專案]。

   ![檢視 [建立新專案] 視窗](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [建立新專案] 視窗中，在搜尋方塊內輸入或鍵入 *Windows Forms*。 接下來，從語言清單中選擇 **Visual Basic**，然後從平台清單中選擇 **Windows**。 

   在您套用語言和平台的篩選條件之後，請選擇 [Windows Forms 應用程式 (.NET Framework)] 範本，然後選擇 [下一步]。

   ![選擇 Windows Forms 應用程式 (.NET Framework) 的 Visual Basic 專案範本](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > 如果您未看到 [Windows Forms 應用程式 (.NET Framework)] 範本，您可以從 [建立新專案] 視窗中安裝。 在 [找不到你要尋找的項目嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 接下來，在 Visual Studio 安裝程式中選擇 **.NET 桌面開發**工作負載。
   > 
   > ![Visual Studio 安裝程式中的 .NET Core 工作負載](../ide/media/install-dot-net-desktop-env.png)
   >
   > 接著，選擇Visual Studio 安裝程式中的 [修改] 按鈕。 系統可能會提示您儲存工作，若收到提示，請依提示執行。 接下來，選擇 [繼續] 以安裝工作負載。 

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 *PictureViewer*。 接著，選擇 [建立]。

::: moniker-end

Visual Studio 會為您的程式建立方案。 方案會做為您程式所需的全部專案和檔案的容器。 本教學課程稍後將會詳細說明這些詞彙。

## <a name="about-the-windows-forms-application-project"></a>關於 Windows Forms 應用程式專案

1. 開發環境包含三個視窗：主視窗、[方案總管] 和 [屬性] 視窗。

     如果遺漏任一個視窗，請還原成預設視窗版面配置，方法是在功能表列上依序選擇 [視窗] > [重設視窗版面配置]。 您也可以使用功能表命令顯示視窗。 在功能表列上，依序選擇 [檢視] > [屬性視窗] 或 [方案總管]。 如果有任何其他視窗開啟，請選擇視窗右上角的 [關閉] (x) 按鈕將視窗關閉。

    ::: moniker range="vs-2017"

    - **主視窗**：您將在這個視窗中進行大部分的工作，例如，使用表單和編輯程式碼。 視窗在 [表單編輯器] 中顯示表單。 視窗頂端會出現 [起始頁] 索引標籤和 [Form1.cs [Design]] 索引標籤 (在 Visual Basic 中，索引標籤名稱的結尾是 *.vb*，而不是 *.cs*)。

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **主視窗**：您將在這個視窗中進行大部分的工作，例如，使用表單和編輯程式碼。 視窗在 [表單編輯器] 中顯示表單。

    ::: moniker-end

    - **方案總管視窗**：在這個視窗中，您可以檢視和巡覽至方案中的所有項目。 如果您選擇一個檔案，[屬性] 視窗的內容會隨著變更。 如果您開啟程式碼檔 (在 Visual C# 中結尾為 *.cs*，在 Visual Basic 中則是 *.vb*)，程式碼檔或程式碼檔的設計工具隨即出現。 設計工具是一個視覺化介面，您可以將控制項 (例如按鈕和清單) 加入該介面中。 Visual Studio 表單的設計工具稱為 **Windows Forms 設計工具**。

    - **屬性視窗**：在這個視窗中，您可以變更在其他視窗中所選擇項目的屬性。 例如，如果您選擇 Form1，可以設定 **Text** 屬性變更其標題，也可以設定 **Backcolor** 屬性變更背景色彩。

    > [!NOTE]
    > 方案總管中的第一行會顯示 [方案 'PictureViewer' (1 個專案)]，表示 Visual Studio 已為您建立方案。 方案可以包含多個專案，不過，您將暫時使用只包含一個專案的方案。

1. 在功能表列上，依序選擇 [檔案] > [全部儲存]。

     或者，選擇工具列上的 [全部儲存] 按鈕，如下圖所示。

     ![[全部儲存] 工具列按鈕](../ide/media/express_iconsaveall.png)<br/>
     [全部儲存] 工具列按鈕

     Visual Studio 會自動填入資料夾名稱和專案名稱，然後將專案儲存在專案資料夾中。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要前往下一個教學課程步驟，請參閱[步驟 2：執行程式](../ide/step-2-run-your-program.md)。

- 若要回到概觀主題，請參閱[教學課程 1：建立圖片檢視器](../ide/tutorial-1-create-a-picture-viewer.md)。

## <a name="see-also"></a>另請參閱

- [建立新的 Windows Form](/dotnet/framework/winforms/creating-a-new-windows-form/)