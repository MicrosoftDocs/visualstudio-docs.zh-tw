---
title: 啟用和停用編輯後繼續 |Microsoft Docs
description: 瞭解如何在設計階段停用和啟用 Visual Studio 選項中的 [編輯後繼續]。 [編輯後繼續] 只能用於偵錯組建中。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 261963cbc1aee63374d6a9c147f42678208c39ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384703"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>如何：啟用和停用編輯後繼續 (c #、VB、c + +) 

您可以在設計階段于 [Visual Studio **選項**] 對話方塊中停用或啟用 [**編輯後繼續**]。 [**編輯後繼續**] 只適用于 debug 組建。 如需詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

在原生 c + + 中，[ **編輯後繼續** ] 需要使用 `/INCREMENTAL` 選項。 如需有關 c + + 功能需求的詳細資訊，請參閱這 [篇 blog 文章](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) 和 [編輯後繼續 (c + +) ](../debugger/edit-and-continue-visual-cpp.md)。

**若要啟用或停用 [編輯後繼續]：**

1. 如果您是在調試進程中，請停止調試 (**Debug**  >  **停止調試** 或 **Shift** + **F5**) 。

1. 在 [**工具**  >  **選項**] > (] 或 [**調試**  >  **選項**]) >   >  **[一般] 的 [一般**] 窗格中，選取 [**編輯後繼續**]。

    > [!NOTE]
    > 如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 [編輯後繼續]。 如需詳細資訊，請參閱 [IntelliTrace](../debugger/intellitrace.md)。

1. 針對 c + + 程式碼，請確定已選取 [ **啟用原生編輯後繼續** ]，並設定其他選項：
    - **在 [繼續 (僅限原生) 上套用變更**

      如果選取此選項，當您繼續從中斷狀態進行偵錯工具時，Visual Studio 會自動編譯並套用程式碼變更。 否則，您可以選擇使用 **Debug** apply 套用程式  >  **代碼變更** 來套用變更。

    - **警告過時的程式碼 (僅限原生)**

      如果選取此選項，則會提供有關過時程式碼的警告。

1. 按一下 [確定]  。
