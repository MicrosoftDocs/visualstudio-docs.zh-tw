---
title: 將圖示新增至功能表命令 |Microsoft Docs
description: 瞭解如何將圖示新增至可在 Visual Studio 整合式開發環境中的功能表和工具列上顯示的命令 (IDE) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9f37bd14ed43ab0e165346f8ce09512c3981177
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934360"
---
# <a name="add-icons-to-menu-commands"></a>將圖示新增至功能表命令
命令可以同時出現在功能表和工具列上。 在工具列上，命令通常只會顯示一個圖示 (為了節省空間) 而功能表上的命令通常會同時以圖示和文字顯示。

 圖示的寬度16圖元寬16圖元，可以是8位色深度 (256 色彩) 或32位色彩深度 (true 色彩) 。 建議您偏好32位色彩圖示。 圖示通常會在單一點陣圖中排列成單一水準資料列，但允許多個點陣圖。 這個點陣圖是在 *.vsct* 檔中宣告，以及點陣圖中可用的個別圖示。 如需詳細資訊，請參閱 [點陣圖元素](../extensibility/bitmaps-element.md) 的參考。

## <a name="add-an-icon-to-a-command"></a>將圖示新增至命令
 下列程式假設您有一個具有功能表命令的現有 VSPackage 專案。 若要瞭解如何執行此作業，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

1. 建立色彩深度為32位的點陣圖。 圖示一律為 16 x 16，因此此點陣圖的高度必須是16圖元，而16圖元的寬度必須是16圖元。

     每個圖示都放在單一資料列中彼此旁的點陣圖。 使用 Alpha 色板來指出每個圖示中的透明度位置。

     如果您使用8位的色彩深度，請使用洋紅色， `RGB(255,0,255)` 作為透明度。 不過，建議您偏好32位色彩圖示。

2. 將圖示檔複製到 VSPackage 專案中的 *Resources* 目錄。 在 **方案總管** 中，將圖示新增至專案。  (選取 **資源**]，然後在內容功能表上按一下 [ **新增**]、[ **現有專案**]，然後選取您的圖示檔。 ) 

3. 在編輯器中開啟 *.vsct* 檔案。

4. 加入 `GuidSymbol` 名稱為 **testIcon** 的元素。 建立 guid (**工具**  >  **建立 guid**，然後選取 [登錄 **格式**]，再按一下 [**複製**) 並貼到 `value` 屬性中。 結果看起來應該像這樣：

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. 新增 `<IDSymbol>` 圖示的。 `name`屬性是圖示的識別碼，而則 `value` 表示其在區域上的位置（如果有的話）。 如果只有一個圖示，請加1。 結果看起來應該像這樣：

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. `<Bitmap>`在 .vsct 檔案的區段中建立， `<Bitmaps>` 以代表包含圖示的點陣圖。 

    - 將 `guid` 值設定為 `<GuidSymbol>` 您在上一個步驟中建立的元素名稱。

    - 將 `href` 值設定為點陣圖檔案的相對路徑 (在此案例中為 **資源 \\<圖示檔名稱 \>**。

    - 將 `usedList` 值設定為您稍早建立的 IDSymbol。 這個屬性會指定要在 VSPackage 中使用的圖示清單（以逗號分隔）。 不在清單上的圖示則會排除表單編譯。

         點陣圖區塊看起來應該像這樣：

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. 在現有的 `<Button>` 元素中，將專案設定 `Icon` 為您稍早建立的 GUIDSymbol 和 IDSymbol 值。 以下是具有這些值的 Button 元素範例：

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
