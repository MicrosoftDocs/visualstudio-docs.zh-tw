---
title: 在混合模式中進行 Debug |Microsoft Docs
description: 瞭解如何在呼叫端應用程式專案的屬性頁中， (managed 和機器碼) 啟用混合模式的偵錯工具。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1144fa2f775427a3a46feda46d8bba015e960f2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913249"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>如何：在混合模式中進行調試 (c #、c + +、Visual Basic) 

下列程式說明如何同時啟用 managed 和機器碼的偵錯工具，也稱為混合模式的偵錯工具。 有兩種混合模式的調試案例：

- 呼叫 DLL 的應用程式是以原生程式碼撰寫，且 DLL 是受管理的。

- 呼叫 DLL 的應用程式是以 managed 程式碼撰寫，而 DLL 是在機器碼中。 如需逐步解說此案例的教學課程，請參閱 [Debug managed 和機器碼（原生程式碼](../debugger/how-to-debug-managed-and-native-code.md)）。

您可以在呼叫應用程式專案的 **屬性** 頁中啟用 managed 和原生偵錯工具。 原生和受控應用程式之間的設定不同。

如果您無法存取呼叫應用程式的專案，您可以從 DLL 專案進行 DLL 的偵錯工具。 您不需要混合模式就能只進行 DLL 專案的調試。 如需詳細資訊，請參閱 [如何：從 DLL 專案進行 Debug](../debugger/how-to-debug-from-a-dll-project.md)。

> [!NOTE]
> 根據您的 Visual Studio 設定或版本，您所看到的對話方塊和命令可能會與本文中的不同。 若要變更您的設定，請選擇 [**工具** 匯  >  **入和匯出設定**]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>啟用原生呼叫應用程式的混合模式偵錯工具

1. 在 **方案總管** 中選取 c + + 專案，然後按一下 [**屬性**] 圖示，按下 **Alt** + **鍵**，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 在 [ **\<Project> 屬性頁**] 對話方塊中，展開 [設定 **屬性**]，然後選取 [**調試**]。

1. 將 **偵錯工具類型** 設定為 **混合** 或 **自動**。

1. 選取 [確定]。

   ![啟用混合模式偵錯](../debugger/media/dbg-mixed-mode-from-native.png "啟用混合模式偵錯")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>針對 managed 呼叫應用程式啟用混合模式的偵錯工具

1. 選取 **方案總管** 中的 c # 或 Visual Basic 專案，然後選取 [**屬性**] 圖示，按下 **Alt** + **鍵**，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [ **調試** 程式] 索引標籤，然後選取 [ **啟用原生程式碼調試** 程式]。

1. 關閉 [屬性] 頁面以儲存變更。

   ![啟用機器碼偵錯](../debugger/media/dbg-mixed-mode-from-csharp.png "啟用機器碼偵錯")

> [!NOTE]
> 自 Visual Studio 2017 開始，在多數的 Visual Studio 版本中，您必須使用 *launchSettings.json* 檔案而非使用專案屬性，來針對 .NET Core 應用程式中的機器碼啟用混合模式偵錯。 如需詳細資訊，請參閱 [Debug managed 和機器碼](../debugger/how-to-debug-managed-and-native-code.md)。

## <a name="see-also"></a>另請參閱

- [如何：從 DLL 專案進行偵錯](../debugger/how-to-debug-from-a-dll-project.md)