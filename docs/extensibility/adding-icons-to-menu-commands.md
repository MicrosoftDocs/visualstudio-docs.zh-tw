---
title: 將圖示加入至功能表命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0d6a6cfeb3cb222d2ef58233b072f80e50c8d9e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056428"
---
# <a name="add-icons-to-menu-commands"></a>將圖示加入至功能表命令
命令可以出現在功能表和工具列。 在工具列上很常見的只是圖示 （以節省空間） 時在功能表上顯示命令通常會出現圖示和文字的命令。

 圖示是 16 像素寬 x 16 像素高，而且可以是 8 位元色彩深度 （256 色） 或 32 位元色彩深度 （全彩）。 32 位元色彩圖示較好。 圖示通常會排列在單一的水平資料列，在單一點陣圖，雖然允許多個點陣圖。 中宣告這個點陣圖 *.vsct*檔案以及個別點陣圖中可用的圖示。 請參閱參考[Bitmaps 元素](../extensibility/bitmaps-element.md)如需詳細資訊。

## <a name="add-an-icon-to-a-command"></a>將圖示新增至命令
 下列程序假設您有現有的功能表命令的 VSPackage 專案。 若要了解如何執行這項操作，請參閱[建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。

1. 建立與色彩深度為 32 位元的點陣圖。 圖示永遠是 16 x 16，因此此點陣圖必須是 16 像素高和 16 像素寬的倍數。

     每個圖示都放在彼此相鄰的點陣圖中的單一資料列。 您可以使用 alpha 色頻來表示透明度中每個圖示的位置。

     如果您使用的 8 位元色彩深度時，使用洋紅、 `RGB(255,0,255)`，做為透明。 不過，32 位元色彩圖示為慣用。

2. 圖示檔案複製到*資源*VSPackage 專案中的目錄。 在 [**方案總管] 中**，將圖示新增至專案。 (選取**資源**，然後在內容功能表按一下 **新增**，然後**現有項目**，然後選取您的圖示檔案。)

3. 開啟 *.vsct*在編輯器中的檔案。

4. 新增`GuidSymbol`項目名稱取代**testIcon**。 建立 GUID (**工具** > **建立 GUID**，然後選取**登錄格式**然後按一下**複製**) 並將它貼到  `value`屬性。 結果應該如下所示：

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. 新增`<IDSymbol>`圖示。 `name`屬性是圖示的識別碼和`value`表示功能表列上的位置，如果有的話。 如果有一個圖示，將 1 加入。 結果應該如下所示：

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. 建立`<Bitmap>`中`<Bitmaps>`一節 *.vsct*來代表包含圖示的點陣圖檔案。

    - 設定`guid`值的名稱`<GuidSymbol>`您在上一個步驟中建立的項目。

    - 設定`href`點陣圖檔的相對路徑的值 (在此情況下**資源\\< 圖示檔檔名\>**。

    - 設定`usedList`IDSymbol 您稍早建立的值。 這個屬性會指定要用於 VSPackage 的圖示以逗號分隔清單。 排除的表單編譯是不在清單上的圖示。

         點陣圖區塊看起來應該像這樣：

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. 在現有`<Button>`項目，設定`Icon`GUIDSymbol 和 IDSymbol 值您稍早建立的項目。 以下是範例的按鈕項目使用這些值：

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. 測試您的圖示。 建置此專案並開始偵錯。 在實驗執行個體中，找到的命令。 它應該會顯示圖示您加入。

## <a name="see-also"></a>另請參閱
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [VSCT XML 結構描述參考](../extensibility/vsct-xml-schema-reference.md)