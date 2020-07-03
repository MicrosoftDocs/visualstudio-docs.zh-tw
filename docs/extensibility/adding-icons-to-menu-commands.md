---
title: 將圖示新增至功能表命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9f038dc43c1705a7cef47eb09a17607c535e307
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903439"
---
# <a name="add-icons-to-menu-commands"></a>將圖示新增至功能表命令
命令可以同時出現在功能表和工具列上。 在工具列上，在功能表上只顯示一個圖示（以節省空間）的命令通常會同時出現圖示和文字。

 圖示的寬度為16圖元，高達16圖元，可以是8位色深度（256色彩）或32位色彩深度（true 色彩）。 32位色彩圖示是慣用的。 圖示通常會在單一點陣圖中以單一水準資料列排列，但允許多個點陣圖。 這個點陣圖會在 *.vsct*檔案中宣告，以及點陣圖中可用的個別圖示。 如需詳細資訊，請參閱[點陣圖元素](../extensibility/bitmaps-element.md)的參考。

## <a name="add-an-icon-to-a-command"></a>將圖示新增至命令
 下列程式假設您有一個具有功能表命令的現有 VSPackage 專案。 若要瞭解如何執行這種做法，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

1. 建立色彩深度為32位的點陣圖。 圖示一律為 16 x 16，因此此點陣圖的高度必須為16圖元，寬為16圖元的倍數。

     每個圖示都放在單一資料列中彼此旁的點陣圖上。 使用 Alpha 色板，表示每個圖示中的透明度位置。

     如果您使用8位色彩深度，請使用洋紅， `RGB(255,0,255)` 做為透明度。 不過，我們偏好32位色彩圖示。

2. 將圖示檔複製到 VSPackage 專案中的*Resources*目錄。 在 [**方案總管**中，將圖示新增至專案。 （選取 [**資源**]，然後在內容功能表上按一下 [**新增**]、[**現有專案**]，然後選取您的圖示檔案）。

3. 在編輯器中開啟 *.vsct*檔案。

4. 加入 `GuidSymbol` 名稱為**testIcon**的元素。 建立 guid （[**工具**] [  >  **建立 guid**]，然後選取 [登錄**格式**]，再按一下 [**複製**]），並將它貼到 `value` 屬性中。 結果看起來應該像這樣：

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. `<IDSymbol>`為圖示新增。 `name`屬性是圖示的識別碼，而則 `value` 表示其在帶狀處的位置（如果有的話）。 如果只有一個圖示，請新增1。 結果看起來應該像這樣：

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. `<Bitmap>`在 .vsct 檔案的 `<Bitmaps>` 區段中建立 *.vsct* ，以代表包含圖示的點陣圖。

    - 將 `guid` 值設定為 `<GuidSymbol>` 您在上一個步驟中建立之元素的名稱。

    - 將 `href` 值設定為點陣圖檔案的相對路徑（在此案例中，**資源 \\<圖示檔名稱 \> **。

    - 將 `usedList` 值設定為您稍早建立的 IDSymbol。 這個屬性會指定要在 VSPackage 中使用的圖示清單（以逗號分隔）。 不在清單上的圖示會排除表單編譯。

         點陣圖區塊看起來應該像這樣：

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. 在現有的 `<Button>` 元素中，將 `Icon` 元素設定為您稍早建立的 GUIDSymbol 和 IDSymbol 值。 以下是具有這些值的 Button 元素範例：

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. 測試您的圖示。 建置此專案並開始偵錯。 在實驗實例中，尋找命令。 它應該會顯示您新增的圖示。

## <a name="see-also"></a>另請參閱
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [.VSCT XML 架構參考](../extensibility/vsct-xml-schema-reference.md)
