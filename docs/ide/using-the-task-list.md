---
title: 使用工作清單
description: 瞭解 Visual Studio 中的工作清單可如何協助您更有效率地追蹤和使用程式碼批註。
ms.date: 10/12/2020
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d19794b4fce3e4a1388f864cecf408e0f7e9c53
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189832"
---
# <a name="use-the-task-list"></a>使用工作清單

您可以使用 [工作清單] 來追蹤使用 `TODO` 和 `HACK` 這類語彙基元或自訂語彙基元的程式碼註解，以及管理會直接將您帶往程式碼中預先定義位置的捷徑。 按一下清單中的項目，以移至它在原始程式碼中的位置。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[工作註解 (Visual Studio for Mac)](/visualstudio/mac/task-comments)。

## <a name="the-task-list-window"></a>工作清單視窗

當 [工作清單]  開啟時，會出現在應用程式視窗的底部。

若要開啟 [工作清單]，請選取 [檢視] > [工作清單]，或從鍵盤按 **Ctrl**+**\\**,**T** 鍵。

![工作清單視窗](../ide/media/vs2015_task_list.png)

若要變更清單的排序順序，請選取任一資料行的標頭。 若要進一步精簡搜尋結果，請按 **Shift** 鍵，然後按一下第二個數據行標頭。 或者，在捷徑功能表上，選擇 [排序依據]，然後選擇一個標頭。 若要進一步精簡搜尋結果，請按 **Shift** 鍵並選擇第二個標頭。

若要顯示或隱藏資料行，請在捷徑功能表上，選擇 [顯示資料行]。 選取要顯示或隱藏的資料行。

若要變更資料行的順序，請將任一資料行標頭拖曳至您想要的位置。

## <a name="user-tasks"></a>使用者工作

使用者工作功能已在 Visual Studio 2015 中移除。 當您開啟的方案有來自 Visual Studio 2013 和更舊版本的使用者工作資料時，*.suo* 檔案中的使用者工作資料並不會受影響，但使用者工作不會顯示在工作清單中。

如果想要繼續存取及更新您的使用者工作資料，請在 Visual Studio 2013 中開啟專案，然後將任何使用者工作的內容複製到您的慣用專案管理工具 (例如 Team Foundation Server)。

## <a name="tokens-and-comments"></a>語彙基元和註解

[工作清單] 中也會顯示程式碼中的註解，其前面會有註解標記和預先定義的語彙基元。 例如，下列 C# 註解有三個不同的部分：

- 註解資料標記 (`//`)

- 語彙基元，例如 (`TODO`)

- 註解 (其餘的文字)

```csharp
// TODO: Load state from previously suspended application
```

因為 `TODO` 是預先定義的語彙基元，所以此註解會顯示為清單中的 `TODO` 工作。

### <a name="custom-tokens"></a>自訂權杖

根據預設，Visual Studio 會包含下列語彙基元：`HACK`、`TODO`、`UNDONE`及 `UnresolvedMergeConflict`。 它們不區分大小寫。 您也可以建立自己的自訂語彙基元。

> [!NOTE]
> 預設權杖僅適用于 C/c + +、c # 及 VB 語言。 若要為其他程式設計語言建立您自己的權杖，請使用下列步驟。

建立自訂語彙基元：

1. 在 [工具] 功能表上，選擇 [選項]。

2. 開啟 [ **環境** ] 資料夾，然後選擇 [ **工作清單**]。

   [工作清單選項頁面](../ide/reference/task-list-environment-options-dialog-box.md)隨即顯示。

   ![Visual Studio 工作清單](../ide/media/vs2015_task_list_options.png)

3. 在 [名稱] 文字方塊中輸入您的權杖名稱，例如 **BUG**。

4. 在 [ **優先權** ] 下拉式清單中，選擇新語彙基元的預設優先權。

5. 選擇 [新增]  。

> [!TIP]
> 輸入名稱後，[新增] 按鈕即變成啟用狀態。 您必須在按一下 [新增] 之前輸入名稱。

### <a name="c-todo-comments"></a>C++ TODO 註解

[工作清單]  中預設會顯示 C++ TODO 註解。

若要關閉 C++ TODO 命令，請在 [工具] 功能表上，選擇 [選項] > [文字編輯器] > [C/C++] > [檢視] > [列舉註解工作]，然後將值設定為 **false**。

## <a name="shortcuts"></a>捷徑

「捷徑」是 [工作清單] 中會追蹤的程式碼中書籤。 它的圖示與一般書籤不同。 按兩下 [工作清單]  中的捷徑，即可移至程式碼中對應的位置。

![Visual Studio 工作清單捷徑圖示](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>建立捷徑

若要建立捷徑，請將指標插入要放置捷徑的程式碼中。 選擇 [**編輯**  >  **書簽**  >  **加入] 工作清單快捷方式**，或按 **ctrl** + **K**、 **ctrl** + **H**。

若要在程式碼中巡覽捷徑，請在清單中選擇捷徑，然後從捷徑功能表中選擇 [下一個工作]  或 [上一個工作]  。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、工作清單](../ide/reference/task-list-environment-options-dialog-box.md)
- [工作註解 (Visual Studio for Mac)](/visualstudio/mac/task-comments)
