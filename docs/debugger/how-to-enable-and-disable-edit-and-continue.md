---
title: 如何-啟用和停用編輯後繼續 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 1907a67412a787148da7a6679e173383e2bb7423
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349662"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>如何：啟用和停用編輯後繼續（c #、VB、c + +）

在設計階段，您可以在 [Visual Studio**選項**] 對話方塊中停用或啟用 [**編輯後繼續**]。 [**編輯後繼續**] 僅適用于 debug 組建。 如需詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

針對原生 c + +，[**編輯後繼續**] 需要使用 `/INCREMENTAL` 選項。 如需 c + + 中功能需求的詳細資訊，請參閱這[篇 blog 文章](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)和[編輯後繼續（c + +）](../debugger/edit-and-continue-visual-cpp.md)。

**若要啟用或停用 [編輯後繼續]：**

1. 如果您是在調試進程中，請停止調試（[**調試**] [  >  **停止調試**] 或**Shift** + **F5**）。

1. 在 [**工具**  >  **選項**] > （或 [**調試**  >  **選項**]） > **Debugging**  >  **[一般**]，然後在右窗格中選取 [**編輯後繼續**]。

    > [!NOTE]
    > 如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 [編輯後繼續]。 如需詳細資訊，請參閱[IntelliTrace](../debugger/intellitrace.md)。

1. 若為 c + + 程式碼，請確定已選取 [**啟用原生編輯後繼續**]，並設定其他選項：
    - **繼續時套用變更（僅限機器碼）**

      如果選取此選項，當您繼續從中斷狀態進行偵錯工具時，Visual Studio 會自動編譯並套用程式碼變更。 否則，您可以選擇使用 [ **Debug**] [套用程式  >  **代碼變更**] 來套用變更。

    - **警告過時程式碼（僅限原生）**

      若選取此選項，會提供有關過時程式碼的警告。

1. 按一下 [確定]。
