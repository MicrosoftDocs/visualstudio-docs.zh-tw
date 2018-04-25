---
title: 使用工作清單 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef9b3904ce06c498518d55b0d62b8e9393c75239
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-task-list"></a>使用工作清單

使用 [工作清單]  追蹤使用 `TODO` 和 `HACK`等語彙基元或自訂語彙基元的程式碼註解，以及管理會引導您直接移至程式碼中預先定義位置的捷徑。 按一下清單中的項目，以移至它在原始程式碼中的位置。

## <a name="the-task-list-window"></a>工作清單視窗

當 [工作清單]  開啟時，會出現在應用程式視窗的底部。

### <a name="to-open-the-task-list"></a>開啟工作清單

- 在 [檢視] 功能表上，選擇 [工作清單]\(鍵盤：Ctrl+\\、T)。

    ![[工作清單] 視窗](../ide/media/vs2015_task_list.png "vs2015_task_list")

### <a name="to-change-the-sort-order-of-the-list"></a>變更清單的排序順序

- 按一下任一資料行的標題。 若要進一步精簡搜尋結果，請按 Shift 鍵再按一下第二個資料行標頭。

     或者，在捷徑功能表上，選擇 [ **排序依據**]，然後選擇標題。 若要進一步精簡搜尋結果，請按 Shift 鍵並選擇第二個資料行標題。

### <a name="to-show-or-hide-columns"></a>顯示或隱藏資料行

- 在捷徑功能表上，選擇 [ **顯示行**]。 選擇要顯示或隱藏的資料行。

### <a name="to-change-the-order-of-the-columns"></a>變更欄位順序

- 將任一個資料行標頭拖曳到想要的位置。

## <a name="user-tasks"></a>使用者工作

從 Visual Studio 2015 開始，已移除使用者工作功能。 當您開啟的解決方案有 Visual Studio 2013 和較早版本的使用者工作資料時，.suo 檔案中的使用者工作資料不會受影響，但使用者工作不會顯示在工作清單中。

如果您想要繼續存取及更新您的使用者工作資料，您應該在 Visual Studio 2013 中開啟專案，並將任何使用者工作的內容複製到您的慣用的專案管理工具 (例如 Team Foundation Server)。

## <a name="tokens-and-comments"></a>語彙基元和註解

程式碼中的註解前方會有一個註解標記，而預先定義的語彙基元也會出現在 [ **工作清單** ] 視窗中。 例如，下列 C# 註解有三個不同的部分：

- 註解資料標記 (`//`)

- 語彙基元，例如 (`TODO`)

- 註解 (其餘的文字)

```csharp
// TODO: Load state from previously suspended application
```

因為 `TODO` 是預先定義的語彙基元，所以此註解會顯示為清單中的 `TODO` 工作。

###  <a name="customTokens"></a> 自訂權杖

根據預設，Visual Studio 包含下列語彙基元：HACK、TODO、UNDONE、NOTE。 這些語彙基元不區分大小寫。

您也可以建立自己的自訂語彙基元。

#### <a name="to-create-a-custom-token"></a>要建立自訂的語彙基元

1. 在 [ **工具** ] 功能表上選擇 [ **選項**]。

2. 開啟 [ **環境** ] 資料夾，然後選擇 [ **工作清單**]。

     [工作清單選項頁面](../ide/reference/task-list-environment-options-dialog-box.md)隨即顯示。

     ![Visual Studio 工作清單](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")

3. 在 [語彙基元]  分類的 [名稱]  文字方塊中，輸入您的語彙基元名稱，例如 "BUG"。

4. 在 [ **優先權** ] 下拉式清單中，選擇新語彙基元的預設優先權。 選擇 [ **加入** ] 按鈕。

###  <a name="cppComments"></a> C++ TODO 註解

根據預設，[工作清單]  視窗中會顯示 C++ TODO 註解。 您可以變更此行為。

#### <a name="to-turn-off-c-todo-comments"></a>若要關閉 C++ TODO 註解

在 [工具] 功能表上，選擇 [選項] > [文字編輯器] > [C/C++] > [檢視] > [列舉註解工作]，然後將值設定為 false。

## <a name="shortcuts"></a>快速鍵

*捷徑* 是在 [工作清單] 內所追蹤程式碼中的書籤；它的圖示與一般書籤不同。 按兩下 [ **工作清單** ] 中的捷徑可移至程式碼中對應的位置。

![Visual Studio 工作清單捷徑圖示](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")

### <a name="to-create-a-shortcut"></a>建立捷徑

若要建立捷徑，請將指標插入要放置捷徑的程式碼中。 選擇 [編輯] > [書籤] > [新增工作清單捷徑]，或按 **Ctrl** + **K**、**Ctrl** + **H**。

若要在程式碼中巡覽捷徑，請在清單中選擇捷徑，然後從捷徑功能表中選擇 [下一個工作]  或 [上一個工作]  。

## <a name="see-also"></a>另請參閱

[選項對話方塊、環境、工作清單](../ide/reference/task-list-environment-options-dialog-box.md)