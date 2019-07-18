---
title: HOW TO：在混合模式偵錯 |Microsoft Docs
ms.date: 11/05/2018
ms.topic: conceptual
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
ms.openlocfilehash: f58c51bf1b610375c6204e27d064870ce1f76d04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894374"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>HOW TO：在混合模式偵錯 (C#， C++，Visual Basic)

下列程序說明如何啟用 managed 和原生程式碼在一起，也就是會在混合模式偵錯的偵錯。 有兩種的混合模式偵錯的案例：

- 呼叫 DLL 的應用程式以原生程式碼，並在 managed DLL。

- 呼叫 DLL 的應用程式以 managed 程式碼撰寫，且原生程式碼的 DLL。 會引導您完成此案例的更詳細的教學課程，請參閱[偵錯 managed 和原生程式碼](../debugger/how-to-debug-managed-and-native-code.md)。

您可以讓呼叫的應用程式專案中的 managed 和原生偵錯工具**屬性**頁面。 原生和 managed 應用程式之間的不同設定。

如果您沒有存取呼叫端應用程式專案，您可以偵錯 DLL 專案的 DLL。 您不需要混合的模式偵錯 DLL 專案。 如需詳細資訊，請參閱[如何：從 DLL 專案進行偵錯](../debugger/how-to-debug-from-a-dll-project.md)。

> [!NOTE]
> 在本文中，根據您的 Visual Studio 設定或版本中的可能會與不同的對話方塊和命令，您會看到。 若要變更您的設定，請選擇**工具** > **匯入和匯出設定**。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>啟用混合模式偵錯原生的呼叫端應用程式

1. 選取C++專案中**方案總管**，按一下 **屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下，然後選擇 **屬性**。

1. 在  **\<專案 > 屬性頁**對話方塊方塊中，展開**組態屬性**，然後選取**偵錯**。

1. 將**偵錯工具類型**設定為**混合**或**自動**。

1. 選取 [確定]  。

   ![啟用混合的模式偵錯](../debugger/media/dbg-mixed-mode-from-native.png "啟用混合的模式偵錯")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>啟用混合模式偵錯 managed 呼叫端的應用程式

1. 中，選取 C# 或 Visual Basic 專案**方案總管**，然後選取**屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下並選擇 **屬性**。

1. 選取 **偵錯**索引標籤，然後按**啟用機器碼偵錯**。

1. 關閉 [屬性] 頁面，以儲存變更。

   ![啟用機器碼偵錯](../debugger/media/dbg-mixed-mode-from-csharp.png "啟用機器碼偵錯")

> [!NOTE]
> 自 Visual Studio 2017 開始，在多數的 Visual Studio 版本中，您必須使用 *launchSettings.json* 檔案而非使用專案屬性，來針對 .NET Core 應用程式中的機器碼啟用混合模式偵錯。 如需詳細資訊，請參閱 <<c0> [ 偵錯 managed 和原生程式碼](../debugger/how-to-debug-managed-and-native-code.md)。

## <a name="see-also"></a>另請參閱

- [如何：從 DLL 專案進行偵錯](../debugger/how-to-debug-from-a-dll-project.md)