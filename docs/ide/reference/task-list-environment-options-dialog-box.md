---
title: 選項對話方塊、環境、工作清單
description: 瞭解如何使用 [環境] 區段中的 [工作清單] 頁面來新增、刪除及變更產生工作清單提醒的註解標記。
ms.custom: SEO-VS-2020
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59eba4addc21c47db19de212c527e744428973f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838362"
---
# <a name="options-dialog-box-environment--task-list"></a>選項對話方塊：環境 \> 工作清單

此 [選項] 頁面可讓您新增、刪除和變更產生 [工作清單] 提醒的註解語彙基元。 若要顯示這些設定，請從 [工具] 功能表中選取 [選項]，並展開 [環境] 資料夾，然後選擇 [工作清單]。

## <a name="task-list-tokens"></a>工作清單語彙基元

如果您在程式碼中插入的註解文字開頭是 [語彙基元清單] 中的語彙基元，則只要開啟檔案進行編輯，[工作清單] 就會將註解顯示為新項目。 按一下 [工作清單] 項目，直接跳到程式碼中的註解行。 如需詳細資訊，請參閱[使用工作清單](../../ide/using-the-task-list.md)。

語彙基元清單\
顯示語彙基元清單，並讓您加入或移除自訂語彙基元。 註解語彙基元在 C# 和 C++ 中是區分大小寫的，但在 Visual Basic 中則不區分。

> [!NOTE]
> 如果您鍵入的語彙基元未與工作清單中所顯示的語彙基元完全相符，則註解工作將不會顯示在 [工作清單] 中。

優先順序\
設定使用所選取語彙基元的工作優先權 (低、普通或高)。 以此語彙基元開頭的工作註解會在 [工作清單] 中自動獲指派指定的優先權。

名稱\
在這裡輸入語彙基元字串，然後按一下 [新增]，將字串新增至語彙基元清單。

新增\
當您輸入新的 [名稱] 時就會啟用。 按一下可使用 [名稱] 和 [優先權] 欄位中所輸入的值，來新增語彙基元字串。

刪除\
按一下可從語彙基元清單刪除所選取的語彙基元。 您無法刪除預設的註解語彙基元。

變更\
按一下可使用 [名稱] 和 [優先權] 欄位中所輸入的值，來變更現有的語彙基元。

> [!NOTE]
> 您無法重新命名或刪除預設的註解語彙基元，但可以變更其優先權層級。

## <a name="see-also"></a>另請參閱

- [使用工作清單](../../ide/using-the-task-list.md)
- [在程式碼中設定書簽](../../ide/setting-bookmarks-in-code.md)
