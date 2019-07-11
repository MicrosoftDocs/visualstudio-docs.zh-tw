---
title: 使用 Visual Studio for Mac Tools for Unity
description: 本指南描述如何使用 Visual Studio for Mac Tools for Unity 延伸模組
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: daffb7721164ae49888a894bec7cad3ac74801a4
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692210"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>使用 Visual Studio for Mac Tools for Unity

在本節中，您將了解如何使用 Visual Studio for Mac Tools for Unity 的整合和生產力功能，以及如何針對 Unity 開發使用 Visual Studio for Mac 偵錯工具。

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中開啟 Unity 指令碼

將 Visual Studio for Mac [設定為 Unity 的外部指令碼編輯器](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac)之後，在開啟所選擇指令碼的情況下，從 Unity 編輯器中開啟任何指令碼將會自動啟動或切換至 Visual Studio for Mac。

或者，從 Unity 的 [資產]  功能表中選取 [Open C# Project] (開啟 C# 專案)  ，也可以在原始檔編輯器中未開啟任何指令碼的情況下開啟 Visual Studio for Mac。

![開啟 C# 專案](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Unity 文件存取

Visual Studio for Mac Tools for Unity 包含存取 Unity API 文件的捷徑。 若要從 Visual Studio for Mac 存取 Unity API 文件，請將游標放在您要了解的 Unity API 上方，然後按 **⌘ 命令 + ‘** 。

## <a name="intellisense-for-unity-messages"></a>Unity 訊息的 IntelliSense
Unity 引擎會將訊息廣播到 MonoBehaviour 指令碼，讓開發人員可以撰寫回應訊息的程式碼，例如 OnMouseDown、OnTriggerEnter 等等。因為這些不是基底 MonoBehaviour 類別中的虛擬方法，所以有些 IDE (例如 MonoDevelop) 缺乏 Unity 訊息的程式碼完成功能。

不過，Visual Studio for Mac Tools for Unity 會將其 IntelliSense 功能擴充為 Unity 訊息。 這可在 MonoBehaviour 指令碼中輕鬆地實作 Unity 訊息，並協助了解 Unity API。 使用適用於 Unity 訊息的 IntelliSense：

1. 將游標放在衍生自 MonoBehaviour 之類別主體內的新行。

2. 開始鍵入 Unity 訊息的名稱，例如 `OnTriggerEnter`。

3. 已鍵入 "**ont**" 字母之後，會出現 IntelliSense 建議清單。

   ![Using IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. 有三種方式可以變更清單上的選項：

   * 使用向上  和向下  方向鍵。

   * 使用滑鼠按一下所需的項目。

   * 繼續鍵入所需項目的名稱。

5. IntelliSense 可以插入選取的 Unity 訊息，包含任何必要參數：

   * 按 **Tab**。

   * 按 **Return**。

   * 按兩下選取的項目。

   ![從 IntelliSense 插入 Unity 訊息](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>新增 Unity 檔案和資料夾

雖然您一律可以在 Unity 編輯器中將新檔案新增至 Unity 專案，但是 Visual Studio for Mac 允許在 Visual Studio 內輕鬆地建立新的 Unity 指令碼、著色器、結構、列舉與資料夾。

### <a name="add-a-new-c-monobehaviour-script"></a>新增 C# MonoBehaviour 指令碼

若要新增 C# MonoBehaviour 指令碼，請以滑鼠右鍵按一下 [資產]  資料夾或它在 Solution Pad 中的其中一個子目錄，然後選取 [新增] > [New MonoBehaviour] (新增 MonoBehaviour)  。

![新增 MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>新增 Unity 著色器

若要新增 Unity 著色器，請以滑鼠右鍵按一下 [資產]  資料夾或 Solution Pad 中的子目錄，然後選取 [新增] > [新增著色器]  。

### <a name="add-a-new-folder"></a>新增資料夾

若要新增資料夾，請以滑鼠右鍵按一下 [資產]  資料夾或 Solution Pad 中的子目錄，然後選取 [新增] > [新增資料夾]  。

這些新增作業會反映在 Unity 編輯器的 [專案] 視窗中。

### <a name="to-rename-a-file-or-folder"></a>重新命名檔案或資料夾
**以滑鼠右鍵按一下** Solution Pad 中要重新命名的項目，然後選取 [重新命名]  。

> [!NOTE]
> 如果您的新 Unity 專案沒有指令碼，而且 [資產] 資料夾未顯示在 Visual Studio for Mac 的 Solution Pad 中，請從 Unity 編輯器新增初始 C# 指令碼。

## <a name="unity-debugging"></a>Unity 偵錯

Unity 專案可以使用 Visual Studio for Mac 進行偵錯。

### <a name="start-debugging"></a>開始偵錯

啟動偵錯：

1. 按一下 [播放]  按鈕，或者鍵入 **Command + Return** 或 **F5**，以將 Visual Studio 連線至 Unity。

   ![在 Visual Studio 中按一下 [播放]](media/using-vsmac-tools-unity-image5.png)

2. 切換至 Unity，然後按一下 [播放]  按鈕，以在編輯器中執行遊戲。

   ![在 Unity 中按一下 [播放]](media/using-vsmac-tools-unity-image6.png)

3. 如果遊戲在連線至 Visual Studio 時於 Unity 編輯器中執行，則遇到的任何中斷點都會暫停執行遊戲，並啟動遊戲在 Visual Studio for Mac 中叫用中斷點的一行程式碼。

### <a name="start-debugging-in-a-single-step"></a>在單一步驟中啟動偵錯

選擇 [附加至 Unity 並試玩]  組態，可直接從 Visual Studio for Mac 在單一步驟中啟動偵錯和播放 Unity 編輯器。

![選取 [附加至 Unity 並試玩]](media/using-vsmac-tools-unity-image8.png)

### <a name="stop-debugging"></a>停止偵錯

停止偵錯：

1. 在 Visual Studio for Mac 中按一下 [停止]  按鈕，或按 **Shift + Command + Return**。

   ![在 Visual Studio 中按一下 [停止]](media/using-vsmac-tools-unity-image7.png)

> [!NOTE]
> 如果您已使用 [附加至 Unity 並試玩]  組態來啟動偵錯，則 [停止]  按鈕也會停止 Unity。

若要深入了解 Visual Studio for Mac 中的偵錯，請參閱 [Using the debugger](debugging.md) (使用偵錯工具)。
