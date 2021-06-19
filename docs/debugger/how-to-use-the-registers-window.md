---
title: 在偵錯工具中查看暫存器值 |Microsoft Docs
description: 在 Visual Studio 的 [暫存器] 視窗中，查看暫存器值。 在偵錯工具期間，登錄值會隨著程式碼在您的應用程式中執行而變更。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2648f74453f51cd8d655ccb0c2344eb1030c1ed
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385392"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>在 [暫存器] 視窗中查看暫存器值， (c #、c + +、Visual Basic、F # ) 

[暫存器] 視窗 **會在 Visual Studio** 的偵測期間顯示暫存器內容。 暫存器的基本概念的高階簡介及 **註冊**] 視窗中，請參閱 [偵錯基本概念： 暫存器視窗](../debugger/debugging-basics-registers-window.md)。

> [!NOTE]
> 腳本或 SQL 應用程式無法使用註冊資訊。

在偵錯工具期間，登錄值會隨著程式碼在您的應用程式中執行而變更。 最近 **變更的值會在 [緩存** 器] 視窗中以紅色顯示。

為了減少雜亂的情況，[暫存器] 視窗會依據平台和處理器類型，將暫存器分為不同的群組。 您可以顯示或隱藏註冊群組。 如需詳細資訊，請參閱[如何：顯示和隱藏暫存器群組](../debugger/how-to-display-and-hide-register-groups.md)。

如需您在 [暫存器 **] 視窗中** 看到之旗標的詳細資訊，請參閱關於暫存器 [視窗](../debugger/debugging-basics-registers-window.md)

您可以編輯暫存器值。 如需詳細資訊，請參閱 [如何：編輯](../debugger/how-to-edit-a-register-value.md)暫存器值。

**開啟註冊視窗**

1. 啟用位址層級的偵錯工具，方法是選取 [**工具**] (中的 [**啟用位址層級的偵錯工具**] 或 [ **Debug**) >**選項**  >  ****]

1. 當偵錯工具正在執行或中斷點時，請選取 [ **Debug** Windows 暫存器]  >    >  ****，或按下 **Alt** + **5**。

>[!NOTE]
>對話方塊和功能表命令可能會根據您的 Visual Studio 版本或設定而有所不同。 若要變更您的設定，請選取 [Visual Studio **工具**] 功能表上的 [匯 **入和匯出設定**]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

### <a name="see-also"></a>另請參閱

- [調試基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)
- [在偵錯工具中查看資料](../debugger/viewing-data-in-the-debugger.md)
