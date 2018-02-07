---
title: "使用 C# 來擷取介面 | Microsoft Docs"
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
- vs.csharp.refactoring.extractinterface
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 0e763bacb6d900fea251b3c41d33fb464479f2c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="extract-an-interface-in-c"></a>使用 C# 來擷取介面 #

**功能：**讓您使用來自類別、結構或介面的現有成員來建立介面。

**時機：**您有數個類別、結構或介面，而它們具有可設為通用並供其他類別、結構或介面使用的方法。

**原因：**介面是適用於物件導向設計的絕佳建構。  想像您有各種動物的類別 (Dog、Cat、Bird) ，這些類別可能都有通用的方法，例如 Eat、Drink、Sleep。  使用一個像是 IAnimal 的介面將可讓 Dog、Cat 及 Bird 有一個適用於這些方法的通用「簽章」。

**做法：**

1. 醒目標示要作為動作執行對象的類別名稱，或直接將文字游標放在類別名稱中的某處。

   ![醒目標示的程式碼](media/extractinterface-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **CTRL+R**，再按 **CTRL+I**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取介面]。
   * **滑鼠**
     * 選取 [編輯] > [重構] > [擷取介面]。
     * 在類別名稱上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取介面]。

1. 在 [擷取介面] 快顯對話方塊中，輸入所要求的資訊：![擷取介面](media/extractinterface-dialog-cs.png)
   | 欄位 | 描述 |
   | --- | --- |
   | **新介面名稱** | 要建立的介面名稱。 這會預設為 I*ClassName*，其中 *ClassName* 是您在上面選取的類別名稱。 |
   | **新檔名** | 所將產生之將包含介面的檔案名稱。 與介面名稱一樣，這會預設為 I*ClassName*，其中 *ClassName* 是您在上面選取的類別名稱。 |
   | **選取公用成員以形成介面** | 要擷取到介面中的項目。  您可以視需要選取所需數量的項目。 |

1. 按一下 [確定 **Deploying Office Solutions**]。

   系統將會在所指定名稱的檔案中立即建立介面。  此外，您選取的類別現在將實作該介面。

   ![產生的類別](media/extractinterface-class-cs.png)
   ![產生的介面](media/extractinterface-interface-cs.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)