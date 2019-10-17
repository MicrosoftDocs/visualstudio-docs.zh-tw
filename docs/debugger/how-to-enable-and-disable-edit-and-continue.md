---
title: 如何：啟用和停用編輯後繼續 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
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
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430530"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>如何：啟用和停用編輯後繼續（C#，VB， C++）

在設計階段，您可以在 [Visual Studio**選項**] 對話方塊中停用或啟用 [**編輯後繼續**]。 [編輯後繼續] 只能用於偵錯組建中。 如需詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

針對 [ C++原生]，[**編輯後繼續**] 需要使用 [`/INCREMENTAL`] 選項。 如需中C++功能需求的詳細資訊，請參閱這[篇 Blog 文章](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)和[編輯C++後繼續（）](../debugger/edit-and-continue-visual-cpp.md)。

**若要啟用或停用 [編輯後繼續]：**

1. 如果您是在調試階段中，請停止調試（**Debug** > **停止調試**或**Shift**+**F5**）。

1. 在 **[工具**]  > **選項**> （或**Debug** > **選項**） >**調試** > **一般**，請在右窗格中選取 [**編輯後繼續**]。

    > [!NOTE]
    > 如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 [編輯後繼續]。 如需詳細資訊，請參閱[IntelliTrace](../debugger/intellitrace.md)。

1. 針對C++程式碼，請確定已選取 [**啟用原生編輯後繼續**]，並設定其他選項：
    - **繼續時套用變更 (僅限原生)**

      如果選取此選項，當您繼續從中斷狀態進行偵錯工具時，Visual Studio 會自動編譯並套用程式碼變更。 否則，您可以選擇使用**Debug**來套用變更  >  會套用程式**代碼變更**。

    - **警告出現過時的程式碼 (僅限原生)**

      若選取此選項，會提供有關過時程式碼的警告。

1. 按一下 [確定]。
