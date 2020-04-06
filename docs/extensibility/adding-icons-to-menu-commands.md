---
title: 加入選單指令加入圖示 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740149"
---
# <a name="add-icons-to-menu-commands"></a>加入選單指令加入圖示
命令可以同時出現在菜單和工具列上。 在工具列上,通常只顯示一個圖示(以節省空間)的命令,而在功能表上,命令通常同時顯示一個圖示和文本。

 圖示寬 16 像素 x 16 像素高,可以是 8 位顏色深度(256 種顏色)或 32 位顏色深度(真色)。 32 位顏色圖示優先。 圖示通常排列在單個位圖中的單個水準行中,儘管允許多個位圖。 此點陣圖在 *.vsct*檔中聲明,以及點陣圖中可用的單個圖示。 有關詳細資訊,請參閱[Bitmap 元素](../extensibility/bitmaps-element.md)的引用。

## <a name="add-an-icon-to-a-command"></a>加入命令加入圖示
 以下過程假定您具有具有功能表命令的現有 VSPackage 專案。 要瞭解如何執行此操作,請參考[選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

1. 創建顏色深度為 32 位元的點陣圖。 圖示始終為 16 x 16,因此此位圖必須高 16 像素,並且倍數為 16 像素寬。

     每個圖示都放在一行的點陣圖上。 使用 Alpha 通道指示每個圖示中的透明度位置。

     如果使用 8 位顏色深度,請使用`RGB(255,0,255)`品紅色 作為透明度。 但是,32 位顏色圖示是首選。

2. 將圖示檔案複製到 VSPackage 專案中的 *「資源」* 目錄。 在**解決方案資源管理員**中,將圖示添加到專案中。 (選擇 **"資源**",並在上下文選單上單擊"**添加**",然後"**添加現有專案**",然後選擇圖示檔。

3. 開啟編輯器中的 *.vsct*檔案。

4. 添加名稱`GuidSymbol`為**testIcon**的元素。 創建 GUID(**工具** > **建立 GUID**,然後選擇**註冊表格式**,然後按下 **「複製**」),並將其貼上`value`到屬性中。 結果應如下所示:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. 為圖示`<IDSymbol>`添加 a。 屬性`name`是圖示的 ID,指示`value`其在條帶上的位置(如果有)。 如果只有一個圖示,則添加 1。 結果應如下所示:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. 在`<Bitmap>``<Bitmaps>`*.vsct*檔部分中創建一個,以表示包含圖示的位圖。

    - 將`guid`值設定為在上一步驟`<GuidSymbol>`中 創建的元素的名稱。

    - 將`href`值設定為點陣圖檔的相對路徑 (在本例中 **,資源\\<\>圖示檔名**。

    - 將`usedList`該值設定為您之前創建的 IDSymbol。 此屬性指定要在 VSPackage 中使用的圖示的逗號分隔清單。 清單中未顯示的圖示將排除表單編譯。

         位圖塊應如下所示:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. 在現有`<Button>`元素中,將`Icon`元素設置為您之前創建的 GUIDSymbol 和 IDSymbol 值。 下面是具有這些值的 Button 元素的範例:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. 測試圖示。 建置此專案並開始偵錯。 在實驗實例中,找到命令。 它應顯示您添加的圖示。

## <a name="see-also"></a>另請參閱
- [延伸選單與指令](../extensibility/extending-menus-and-commands.md)
- [VSCT XML 架構參考](../extensibility/vsct-xml-schema-reference.md)
