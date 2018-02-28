---
title: "在 Visual Studio 中擷取介面重構 | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 451b5ccddf6052eca3ae0a19b87076d2fd88a952
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="extract-an-interface-refactoring"></a>擷取介面重構

此重構適用於：

- C#

- Visual Basic

**功能：**讓您使用來自類別、結構或介面的現有成員來建立介面。

**時機：**您有數個類別、結構或介面，而它們具有可設為通用並供其他類別、結構或介面使用的方法。

**原因：**介面是適用於物件導向設計的絕佳建構。 想像您有各種動物的類別 (Dog、Cat、Bird) ，這些類別可能都有通用的方法，例如 Eat、Drink、Sleep。 使用一個像是 IAnimal 的介面將可讓 Dog、Cat 及 Bird 有一個適用於這些方法的通用「簽章」。

## <a name="how-to"></a>操作說明

1. 醒目標示要作為動作執行對象的類別名稱，或直接將文字游標放在類別名稱中的某處。

   - C#: 

    ![醒目提示的程式碼 - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic：

    ![醒目提示的程式碼 - Visual Basic](media/extractinterface-highlight-vb.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
     - 按 **CTRL+R**，再按 **CTRL+I**。 (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     - 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取介面]。
   - **滑鼠**
     - 選取 [編輯] > [重構] > [擷取介面]。
     - 在類別名稱上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取介面]。

1. 在 [擷取介面] 快顯對話方塊中，輸入系統要求的資訊：

   ![擷取介面](media/extractinterface-dialog-cs.png)

   | 欄位 | 描述 |
   | --- | --- |
   | **新介面名稱** | 要建立的介面名稱。 這會預設為 I*ClassName*，其中 *ClassName* 是您在上面選取的類別名稱。 |
   | **新檔名** | 所將產生之將包含介面的檔案名稱。 與介面名稱一樣，這會預設為 I*ClassName*，其中 *ClassName* 是您在上面選取的類別名稱。 |
   | **選取公用成員以形成介面** | 要擷取到介面中的項目。 您可以視需要選取所需數量的項目。 |

1. 選擇 [確定] 。

   系統會在指定名稱的檔案中建立介面。 此外，您選取的類別會實作該介面。

   - C#: 

    ![產生的類別 - C#](media/extractinterface-class-cs.png)
    ![產生的介面 - C#](media/extractinterface-interface-cs.png)

   - Visual Basic：

    ![產生的類別 - Visual Basic](media/extractinterface-class-vb.png)
    ![產生的介面 - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)