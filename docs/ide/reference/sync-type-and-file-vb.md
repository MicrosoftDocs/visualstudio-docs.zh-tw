---
title: "使用 Visual Basic 來同步類型和檔案名稱 | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 93e1b1f446dc330b2c2c1c1e5b36e6a21e64f521
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-visual-basic"></a>使用 Visual Basic 將類型同步至檔案名稱，或將檔案名稱同步至類型

<!-- VERSIONLESS -->
**Visual Studio 2017 及更新版本有提供這項功能。此外，目前還不支援 .NET Standard 專案進行此重構。**

**功能：**讓您將類型重新命名以符合檔案名稱，或將檔案名稱重新命名以符合其包含的類型。

**時機：**您已將檔案或類型重新命名，但尚未更新對應的檔案或類型來使其相符。 

**原因：**將類型放在不同名稱的檔案中 (或反之亦然) 會很難找出所要尋找的項目。  藉由將類型或檔案名稱重新命名，程式碼會變得較容易閱讀及瀏覽。

**做法：**

1. 醒目標示要同步的類型名稱，或將文字游標放在要同步的類型名稱內：

   ![醒目標示的程式碼](media/synctype-highlight-vb.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將檔案重新命名為 *TypeName*.vb]，其中 *TypeName* 是您所選類型的名稱。
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將類型重新命名為 _Filename_]，其中 *Filename* 是目前檔案的名稱。
   * **滑鼠**
     * 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將檔案重新命名為 *TypeName*.vb]，其中 *TypeName* 是您所選類型的名稱。
     * 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將類型重新命名為 _Filename_]，其中 *Filename* 是目前檔案的名稱。

   系統將會立即將類型或檔案重新命名。  在下面的範例中，檔案 **Employee.vb** 已重新命名為 **Person.vb** 以符合類型名稱。

   ![內嵌結果](media/synctype-result-vb.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)
