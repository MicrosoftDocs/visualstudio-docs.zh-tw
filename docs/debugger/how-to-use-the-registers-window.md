---
title: 查看偵錯工具中的暫存器值 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: how-to
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed60b21d7c8e90e18b389a29c3343713ac8ece3d
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348570"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>在 [暫存器] 視窗中查看暫存器值（c #、c + +、Visual Basic、F #）

[暫存器] 視窗**會在 Visual Studio**的調試期間顯示暫存器內容。 暫存器的基本概念的高階簡介及**註冊**] 視窗中，請參閱[偵錯基本概念： 暫存器視窗](../debugger/debugging-basics-registers-window.md)。

> [!NOTE]
> 腳本或 SQL 應用程式無法使用註冊資訊。

在偵測期間，註冊值會隨著程式碼在您的應用程式中執行而變更。 最近變更的值會**在 [緩存**器] 視窗中以紅色顯示。

為了減少雜亂的情況，[暫存器]**** 視窗會依據平台和處理器類型，將暫存器分為不同的群組。 您可以顯示或隱藏暫存器群組。 如需詳細資訊，請參閱[如何：顯示和隱藏暫存器群組](../debugger/how-to-display-and-hide-register-groups.md)。

如需您在 [暫存器] 視窗中看到之旗**標的詳細**資訊，請參閱關於暫存器[視窗](../debugger/debugging-basics-registers-window.md)

您可以編輯暫存器值。 如需詳細資訊，請參閱[如何：編輯](../debugger/how-to-edit-a-register-value.md)暫存器值。

**開啟 [暫存器] 視窗**

1. 啟用位址層級的偵錯工具，方法是選取 [**工具**] （或 [ **Debug**]）中的 [**啟用位址層級的調試**程式] >**選項**  >  **Debugging**

1. 在執行或于中斷點時，請選取 [ **Debug**Windows 暫存器]  >  **Windows**  >  ** **，或按**Alt** + **5**。

>[!NOTE]
>對話方塊和功能表命令可能會根據您的 Visual Studio 版本或設定而有所不同。 若要變更您的設定，請選取 [Visual Studio**工具**] 功能表上的 [匯**入和匯出設定**]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

### <a name="see-also"></a>另請參閱

- [調試基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)
- [在偵錯工具中查看資料](../debugger/viewing-data-in-the-debugger.md)
