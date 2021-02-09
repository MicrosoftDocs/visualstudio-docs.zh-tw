---
title: 自訂功能表與工具列
description: 瞭解如何自訂 Visual Studio 功能表和工具列，並瞭解如何自訂功能表和工具列中包含的任何命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0741a85be90f35e887a40f6ca1c957af8ef3c611
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930313"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>如何：在 Visual Studio 中自訂功能表和工具列

您可以自訂 Visual Studio，不只是可以新增及移除功能表列上的工具列和功能表，還可以新增及移除任何指定工具列或功能表上的命令。

> [!WARNING]
> 在自訂某個工具列或功能表之後，請確認 [自訂] 對話方塊中的核取方塊保持選取。 否則，在關閉並重新開啟 Visual Studio 後，您所做的變更將不會保存下來。

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>在功能表列新增、移除或移動功能表

1. 在功能表列上，選擇 [**工具**  >  **自訂**]。

     [自訂] 對話方塊隨即開啟。

2. 在 [命令] 索引標籤上，保持 [功能表列] 選項按鈕的已選取狀態，以及該選項旁清單中 [功能表列] 的已選取狀態，然後執行下列其中一組步驟：

    - 若要加入功能表，請選擇 [新增功能表] 按鈕，選擇 [修改選取範圍] 按鈕，然後為您要新增的功能表命名。

        ![自訂顯示如何加入功能表的對話方塊](../ide/media/addmenu.png)

    - 若要移除功能表，請在 [控制項] 清單中選擇該功能表，然後選擇 [刪除] 按鈕。

    - 若要在功能表列內移動功能表，請在 [控制項] 清單中選擇該功能表，然後選擇 [上移] 或 [下移] 按鈕。

## <a name="add-remove-or-move-a-toolbar"></a>新增、移除或移動工具列

1. 在功能表列上，選擇 [**工具**  >  **自訂**]。

     [自訂] 對話方塊隨即開啟。

2. 在 [工具列] 索引標籤上，執行下列其中一組步驟：

    - 若要新增工具列，請選擇 [新增] 按鈕，為您要新增的工具列指定一個名稱，然後選擇 [確定] 按鈕。

        ![自訂顯示如何加入工具列的對話方塊](../ide/media/addtoolbar.png)

    - 若要移除自訂工具列，請在 [工具列] 清單中選擇該工具列，然後選擇 [刪除] 按鈕。

        > [!IMPORTANT]
        > 您可以刪除您建立的工具列，但無法刪除預設工具列。

    - 若要將工具列移動至不同的停駐位置，請在 [工具列] 清單中選擇該工具列，選擇 [修改選取範圍] 按鈕，然後在出現的清單中選擇一個位置。

        您也可以拖曳工具列的左邊緣，將它移動至主要停駐區中的任何位置。

        > [!NOTE]
        > 如需如何改善工具列的可用性和協助工具的詳細資訊，請參閱[如何：設定 IDE 協助工具選項](../ide/reference/how-to-set-ide-accessibility-options.md)。

## <a name=""></a><a name="customizing_menu">自訂功能表或工具列</a>

1. 在功能表列上，選擇 [**工具**  >  **自訂**]。

    [自訂] 對話方塊隨即開啟。

2. 在 [命令] 索引標籤上，選擇您要自訂的項目類型選項按鈕。

3. 在該項目類型的清單中，選擇您要自訂的功能表或工具列，然後執行下列其中一組步驟：

    - 若要新增命令，請選擇 [加入命令] 按鈕。

        在 [加入命令] 對話方塊中，選擇 [分類] 清單中的某個項目，選擇 [命令] 清單中的某個項目，然後選擇 [確定] 按鈕。

        ![Visual Studio 中的 [加入命令] 對話方塊](../ide/media/addcommand.png)

    - 若要刪除命令，請在 [控制項] 清單中選擇該命令，然後選擇 [刪除] 按鈕。

    - 若要重新排列命令的順序，請在 [控制項] 清單中選擇命令，然後選擇 [上移] 或 [下移] 按鈕。

    - 若要將命令分組到水平線下方，請在 [控制項] 清單中選擇第一個命令，選擇 [修改選取範圍] 按鈕，然後在出現的功能表中選擇 [開始群組]。

## <a name="reset-a-menu-or-a-toolbar"></a>重設功能表或工具列

1. 在功能表列上，選擇 [**工具**  >  **自訂**]。

    [自訂] 對話方塊隨即開啟。

2. 在 [命令] 索引標籤上，選擇您要重設的項目類型選項按鈕。

3. 在該項目類型的清單中，選擇您要重設的功能表或工具列。

4. 選擇 [修改選取範圍] 按鈕，然後在出現的功能表中選擇 [重設]。

    您也可以選擇 [全部重設] 按鈕，重設所有功能表和工具列。

## <a name="see-also"></a>另請參閱

- [個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)
- [自訂編輯器](../ide/how-to-change-text-case-in-the-editor.md)
