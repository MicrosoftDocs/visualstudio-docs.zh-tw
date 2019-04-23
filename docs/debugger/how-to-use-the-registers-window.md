---
title: 檢視暫存器值中偵錯工具 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
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
ms.openlocfilehash: afcada407060af2072e3cf1c30e86153762890b5
ms.sourcegitcommit: 847d192013eb8225776243045c9b5a53d1ba4a59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2019
ms.locfileid: "59584385"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>檢視暫存器暫存器視窗中的值 (C#， C++，Visual Basic 中， F#)

**註冊**視窗會顯示在 Visual Studio 偵錯期間暫存器內容。 暫存器的基本概念的高階簡介及**註冊**] 視窗中，請參閱[偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)。

> [!NOTE]
> 無法使用的指令碼或 SQL 應用程式註冊資訊。

偵錯期間，註冊值變更，在您的應用程式中執行的程式碼。 最近，已變更的值會出現在紅色**註冊**視窗。

為了減少雜亂的情況，[暫存器] 視窗會依據平台和處理器類型，將暫存器分為不同的群組。 您可以顯示或隱藏暫存器群組。 如需詳細資訊，請參閱[如何：顯示和隱藏暫存器群組](../debugger/how-to-display-and-hide-register-groups.md)。

如需使用旗標的資訊] 所示**註冊**] 視窗中，請參閱[關於暫存器視窗](../debugger/debugging-basics-registers-window.md)

您可以編輯暫存器值。 如需詳細資訊，請參閱[如何：編輯暫存器值](../debugger/how-to-edit-a-register-value.md)。

**若要開啟 [暫存器視窗**

1. 啟用位址層級偵錯，方法是選取**啟用位址層級偵錯**中**工具**(或**偵錯**) >**選項** > **偵錯**。

1. 當偵錯是執行中或在中斷點上時，選取**偵錯** > **Windows** > **註冊**，或按**Alt**+ **5**。

>[!NOTE]
>對話方塊和功能表命令可能會根據您的 Visual Studio 版本或設定不同。 若要變更您的設定，請選取**匯入和匯出設定**在 Visual Studio**工具**功能表。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

### <a name="see-also"></a>另請參閱

- [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
