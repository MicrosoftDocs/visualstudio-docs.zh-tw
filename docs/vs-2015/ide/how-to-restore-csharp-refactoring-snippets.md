---
title: 如何：還原 C# 重構程式碼片段 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ae3f1d74a482192d3782aaa87baa816694abcf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670791"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>如何：還原 C# 重構程式碼片段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C# 重構作業需仰賴在下列目錄中找到的程式碼片段：

 <安裝目錄>** \Microsoft Visual Studio 14.0\VC#\Snippets\\<語言識別碼>** \Refactoring

 如果這個重構目錄或此目錄中的任何檔案已被刪除或損毀，則 C# 重構作業可能無法在 IDE 中運作。 下列程序可協助您還原 C# 重構程式碼片段。

### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>若要透過程式碼片段管理員，驗證 C# 重構程式碼片段是否可用

1. 在 [工具]**** 功能表上，選取 [程式碼片段管理員]****。

2. 在 [程式碼片段管理員]**** 對話方塊中，選取 [語言]**** 下拉式清單中的 [Visual C#]****。

     樹狀檢視資料夾清單應會顯示 [重構]**** 資料夾。

### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>若要還原重構，請參閱程式碼片段管理員中的註解。

1. 如果程式碼片段管理員中的樹狀檢視資料夾清單未顯示 [重構]**** 資料夾，請使用此程序，將重構程式碼片段加回程式碼片段管理員。

2. 在 [工具]**** 功能表上，選取 [程式碼片段管理員]****。

3. 在 [程式碼片段管理員]**** 對話方塊中，選取 [語言]**** 下拉式清單中的 [Visual C#]****。

4. 按一下 [新增] 。 [程式碼片段目錄]**** 對話方塊隨即出現，其有助您尋找並指定要加回程式碼片段管理員的目錄。

5. 找出目錄路徑如下的 [重構]**** 資料夾：

     <安裝目錄>** \Microsoft Visual Studio 14.0\VC#\Snippets\\<語言識別碼>** \Refactoring

     實際路徑類似於下列的預設安裝路徑：

     C:\Program Files\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring。

6. 按一下 [程式碼片段目錄]**** 對話方塊中的 [開啟]****，然後按一下程式碼片段管理員中的 [確定]****。

## <a name="see-also"></a>另請參閱
 [Visual c # 程式碼片段](../ide/visual-csharp-code-snippets.md)[重構 (c # ) ](../csharp-ide/refactoring-csharp.md) [程式碼片段](../ide/code-snippets.md)
