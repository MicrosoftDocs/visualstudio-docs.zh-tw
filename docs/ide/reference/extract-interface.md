---
title: 擷取介面重構
description: 瞭解如何使用 [快速動作與重構] 功能表，利用類別、結構或介面的現有成員來建立介面。
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 13e9b684c81abf491b5836c96190c6a89bdc0643
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617392"
---
# <a name="extract-an-interface-refactoring"></a>擷取介面重構

此重構適用於：

- C#

- Visual Basic

事項 **：** 可讓您使用類別、結構或介面的現有成員來建立介面。

時機 **：** 您有類別、結構或介面中的成員，可由其他類別、結構或介面繼承。

**原因：** 介面是適用於物件導向設計的絕佳建構。 想像您有各種動物的類別 (Dog、Cat、Bird) ，這些類別可能都有通用的方法，例如 Eat、Drink、Sleep。 使用一個像是 IAnimal 的介面將可讓 Dog、Cat 及 Bird 有一個適用於這些方法的通用「簽章」。

## <a name="extract-an-interface-refactoring"></a>擷取介面重構

1. 將游標放在類別名稱中。

   - C#：

       ![醒目提示的程式碼 - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 - Visual Basic](media/extractinterface-highlight-vb.png)

2. 接著，執行下列其中一個動作：

   - **鍵盤**
      - 按 **CTRL+R**，再按 **CTRL+I**。 (根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取介面]。
   - **滑鼠**
      - 選取 [編輯] > [重構] > [擷取介面]。
      - 在類別名稱上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取介面]。

3. 在 [擷取介面] 快顯對話方塊中，輸入系統要求的資訊：

   ![擷取介面](media/extractinterface-dialog-same-file.png)

   | 欄位 | 描述 |
   | - | - |
   | **新介面名稱** | 要建立的介面名稱。 名稱會預設為 I *ClassName*，其中 *ClassName* 是您在上方選取的類別名稱。 |
   | **新檔名** | 產生的檔案名稱，該檔案會包含介面。 與介面名稱一樣，此名稱會預設為 I *ClassName*，其中 *ClassName* 是您在上方選取的類別名稱。 您也可以選取 [Add to current file] \(新增至目前的檔案\) 選項。 |
   | **選取公用成員以形成介面** | 要擷取到介面中的項目。 您可以視需要選取所需數量的項目。 |

4. 選擇 [確定]。

   系統會在指定名稱的檔案中建立介面。 此外，您選取的類別會實作該介面。

   - C#：

      ![產生的類別 - C#](media/extractinterface-class-cs.png)

      ![產生的介面 - C#](media/extractinterface-interface-cs.png)

   - Visual Basic：

      ![產生的類別 - Visual Basic](media/extractinterface-class-vb.png)

      ![產生的介面 - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
