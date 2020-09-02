---
title: 選項對話方塊、環境、工作清單 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72e5f82fa3ca4b7ca909ee07e5b77a31b3e20879
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650967"
---
# <a name="task-list-environment-options-dialog-box"></a>選項對話方塊、環境、工作清單
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

此 [選項] 頁面可讓您新增、刪除和變更產生 [工作清單]**** 提醒的註解語彙基元。 若要顯示這些設定，請從 [工具]**** 功能表中選取 [選項]****，並展開 [環境]**** 資料夾，然後選擇 [工作清單]****。

## <a name="task-list-options"></a>工作清單選項
 確認刪除工作時，當使用者工作從 **工作清單**中刪除時，就會顯示訊息方塊，讓您確認刪除作業。 預設會選取這個選項。

> [!NOTE]
> 若要刪除工作註解，請使用連結尋找註解，然後從程式碼加以移除。

 只有在選取時才顯示檔案名，**工作清單**的 [檔案] 欄只會顯示要編輯**的檔案名，** 而不會顯示其完整路徑。

## <a name="tokens"></a>權杖
 如果您在程式碼中插入的註解文字開頭是 [語彙基元清單]**** 中的語彙基元，則只要開啟檔案進行編輯，[工作清單]**** 就會將註解顯示為新項目。 您可以按一下這個 [工作清單]**** 項目，直接跳到程式碼中的註解行。 如需詳細資訊，請參閱[使用工作清單](../../ide/using-the-task-list.md)。

 [權杖清單] 會顯示權杖清單，並可讓您新增或移除自訂權杖。 註解語彙基元在 Visual C# 和 Visual C++ 中是區分大小寫的，但在 Visual Basic 中則不區分。

> [!NOTE]
> 如果您鍵入的語彙基元未與 [工作清單]**** 中所顯示的語彙基元完全相符，則註解工作將不會顯示在 [工作清單]**** 中。

 優先權：設定使用所選權杖之工作的優先順序。 以此語彙基元開頭的工作註解會在 [工作清單]**** 中自動獲指派指定的優先權。

 名稱：輸入權杖字串。 這會啟用 [新增]**** 按鈕。 在 [新增]**** 上，這個字串會包含在 [語彙基元清單]**** 中，而且以這個名稱開頭的註解將會顯示在 [工作清單]**** 中。

 當您輸入新 **名稱**時，即會啟用 [新增]。 按一下可使用 [名稱]**** 和 [優先權]**** 欄位中所輸入的值，來新增語彙基元字串。

 刪除 [按一下] 可從 **權杖清單**中刪除選取的標記。 您無法刪除預設的註解語彙基元。

 變更 Click，使用 [ **名稱** ] 和 [ **優先順序** ] 欄位中輸入的值來變更現有的權杖。

> [!NOTE]
> 您無法重新命名或刪除預設的註解語彙基元，但可以變更其優先權層級。

## <a name="see-also"></a>另請參閱
 在程式碼[環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)中[使用工作清單](../../ide/using-the-task-list.md)[設定書簽](../../ide/setting-bookmarks-in-code.md)
