---
title: "在適用於 C# 的 Visual Studio 中重構重新命名 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e1325de81e16b0e381f07af4d8073d0a3fa4330c
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="rename-a-code-symbol-in-c"></a>使用 C# 來重新命名程式碼符號 #

**功能：**讓您重新命名程式碼符號 (例如欄位、區域變數、方法、命名空間、屬性及類型) 的識別碼。

**時機：**您想要安全地重新命名某個項目，而無須尋找所有執行個體及複製/貼上新名稱。

**原因：**在整個專案複製並貼上新名稱可能造成錯誤。  這個重構工具將可正確地執行重新命名動作。

**做法：**

1. 醒目標示要重新命名的項目，或將文字游標放在要重新命名的項目內：

   ![醒目標示的程式碼](media/rename-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **CTRL+R**，再按 **CTRL+R**。 (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
   * **滑鼠**
     * 選取 [編輯] > [重構] > [重新命名]。
     * 在程式碼上按一下滑鼠右鍵，然後選取 [重新命名]。

1. 直接輸入新名稱來重新命名項目。

   ![重新命名動畫](media/rename-animated-cs.gif)

   > [!TIP]
   > 您也可以使用出現在 IDE 右上角 [重新命名] 方塊中的核取方塊，以更新註解和其他字串來使用這個新名稱，以及在儲存前先[預覽變更](../../ide/preview-changes.md)。

1. 對變更感到滿意時，按一下 [套用] 按鈕或按 **Enter**，便會認可變更。

> [!NOTE]
> 如果您使用已經存在而會造成衝突的名稱，IDE 中的 [重新命名] 方塊將會警告您。
>
> ![重新命名衝突](media/rename-conflict-cs.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)
