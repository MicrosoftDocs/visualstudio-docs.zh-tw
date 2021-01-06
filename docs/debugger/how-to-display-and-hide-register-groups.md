---
title: 顯示和隱藏註冊群組 |Microsoft Docs
description: '[暫存器] 視窗，如果已啟用位址層級的偵錯工具，就可以使用此視窗，將暫存器組織成群組。 瞭解如何設定要顯示的群組。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c14d325d417606c6945d51d99461d34ccd9a4bc8
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903034"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>如何：顯示和隱藏暫存器群組 (c #、c + +、Visual Basic、F # ) 

只有在透過 [選項] 對話方塊 [一般] 分類的 [偵錯] 節點啟用位址層級偵錯時，才可以使用 [暫存器] 視窗。

為了減少雜亂，[暫存器] 視窗會將暫存器組織成群組。 如果您以滑鼠右鍵按一下 [暫存器] 視窗，將會看到一個包含這些群組的捷徑功能表，您可視需要使用下列程序來顯示或隱藏它們。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="display-or-hide-register-groups"></a>顯示或隱藏註冊群組

1. 在 [暫存器] 視窗上按一下滑鼠右鍵。

2. 在捷徑功能表中選取要顯示或隱藏的暫存器群組。

     捷徑功能表會停用偵錯硬體不支援的暫存器群組，因此不會選取這些群組。

## <a name="see-also"></a>另請參閱

- [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)