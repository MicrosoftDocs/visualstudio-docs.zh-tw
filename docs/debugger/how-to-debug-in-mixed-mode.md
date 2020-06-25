---
title: 如何在混合模式中進行調試 |Microsoft Docs
ms.date: 11/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53a40c4dc615b5e1b6a3caef3a99be5ab0b56327
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350104"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>如何：在混合模式中進行調試（c #、c + +、Visual Basic）

下列程式描述如何同時啟用 managed 和機器碼的偵錯工具，也稱為混合模式的偵錯工具。 有兩種混合模式的調試情況：

- 呼叫 DLL 的應用程式是以機器碼撰寫，而且 DLL 是受管理的。

- 呼叫 DLL 的應用程式是以 managed 程式碼撰寫，而 DLL 則是機器碼。 如需逐步解說此案例的教學課程，請參閱偵錯工具[和原生程式碼](../debugger/how-to-debug-managed-and-native-code.md)。

您可以在呼叫應用程式專案的**屬性**頁中啟用 managed 和原生偵錯工具。 原生和受控應用程式的設定不同。

如果您沒有呼叫應用程式專案的存取權，您可以從 DLL 專案中，對 DLL 進行的偵錯工具。 您不需要混合模式來只對 DLL 專案進行 debug。 如需詳細資訊，請參閱[如何：從 DLL 專案進行調試](../debugger/how-to-debug-from-a-dll-project.md)程式。

> [!NOTE]
> 根據您的 Visual Studio 設定或版本，您所看到的對話方塊和命令可能會與本文中的不同。 若要變更您的設定，請選擇 [**工具**] [匯  >  **入和匯出設定**]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>針對原生呼叫應用程式啟用混合模式的偵錯工具

1. 在**方案總管**中選取 c + + 專案，然後按一下 [**屬性**] 圖示，按**Alt** + **enter**鍵，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 在 [ ** \<Project> 屬性頁**] 對話方塊中，展開 [設定**屬性**]，然後選取 [**調試**]。

1. 將**偵錯工具類型**設定為**混合**或**自動**。

1. 選取 [確定]。

   ![啟用混合模式偵錯](../debugger/media/dbg-mixed-mode-from-native.png "啟用混合模式偵錯")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>針對受管理的呼叫應用程式啟用混合模式的偵錯工具

1. 在**方案總管**中選取 c # 或 Visual Basic 專案，然後選取 [**屬性**] 圖示，按**Alt** + **enter**鍵，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [**調試**程式] 索引標籤，然後選取 [**啟用原生程式碼調試**程式]。

1. 關閉 [屬性] 頁面，以儲存變更。

   ![啟用機器碼偵錯](../debugger/media/dbg-mixed-mode-from-csharp.png "啟用機器碼偵錯")

> [!NOTE]
> 自 Visual Studio 2017 開始，在多數的 Visual Studio 版本中，您必須使用 *launchSettings.json* 檔案而非使用專案屬性，來針對 .NET Core 應用程式中的機器碼啟用混合模式偵錯。 如需詳細資訊，請參閱[偵錯工具管理和機器碼](../debugger/how-to-debug-managed-and-native-code.md)。

## <a name="see-also"></a>另請參閱

- [如何：從 DLL 專案進行偵錯](../debugger/how-to-debug-from-a-dll-project.md)