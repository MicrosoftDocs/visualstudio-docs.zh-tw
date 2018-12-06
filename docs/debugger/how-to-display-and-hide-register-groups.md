---
title: 如何： 顯示和隱藏暫存器群組 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abd617a1b787896f296976ba21f76d3eafbd13c4
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388604"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>如何： 顯示和隱藏暫存器群組 (C#，c + +、 Visual Basic 中， F#)

只有在透過 [選項 **] 對話方塊 [一般**] 分類的 [偵錯 **] 節點啟用位址層級偵錯時，才可以使用 [暫存器**] 視窗。

若要減少雜亂，[暫存器 **] 視窗會將暫存器組織成群組。 如果您以滑鼠右鍵按一下 [暫存器 **] 視窗，將會看到一個包含這些群組的捷徑功能表，您可視需要使用下列程序來顯示或隱藏它們。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 <<c0> [ 重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="display-or-hide-register-groups"></a>顯示或隱藏暫存器群組

1.  在 [暫存器 **] 視窗上按一下滑鼠右鍵。

2.  在捷徑功能表中選取要顯示或隱藏的暫存器群組。

     捷徑功能表會停用偵錯硬體不支援的暫存器群組，因此不會選取這些群組。

## <a name="see-also"></a>另請參閱

- [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)