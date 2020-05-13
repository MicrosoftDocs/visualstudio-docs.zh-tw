---
title: 演練:將自定義 XAML 添加到起始頁 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697683"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>演練:將自訂 XAML 新增到起始頁

本演練演示如何創建包含 Web 瀏覽器的自定義可視化工作室起始頁。

## <a name="add-custom-xaml"></a>新增自訂 XAML

1. 按照[「創建自訂起始頁](../extensibility/creating-a-custom-start-page.md)」中的說明創建起始頁。

2. 在*MainWindow.xaml*檔中,\<查找網格>部分。

3. 在\<\<格線>元素中添加 TabControl>\<元素和 TabItem>,如以下範例所示。

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. 使用開啟新項目\<的按鈕>元素新增\<第 二個 TabItem>:

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>測試自訂起始頁

1. 按 **F5**。

     Visual Studio 的實驗實例將打開,並安裝自定義起始頁,但未選擇。

2. 在可視化工作室的實驗實例中,打開**工具/選項/環境**頁面。

3. 選擇**啟動**。 在 **「自訂起始頁」** 清單中,選擇 *.xaml*檔,然後單擊 **「確定**」。。

4. 在 [檢視] **** 功能表上，按一下 [起始頁] ****。

5. 按下**必應**選項卡。

     您應該會看到必應網頁。

6. 按下 **「我的按鈕」** 選項卡。

     您應該會看到一個 **「我的專案」** 按鈕,該按鈕將打開 **「新專案」** 對話方塊。

7. 關閉實驗實例。

要應用自定義起始頁,請在 **「工具** > **」選項** > **環境**」中,選擇 **「啟動**」。 在 **「自訂起始頁」** 清單中,選擇 *.xaml*檔,然後單擊 **「確定**」。。

## <a name="next-steps"></a>後續步驟

Visual Studio 起始頁現在包含一個選項卡,該選項卡顯示 Web 瀏覽器選項卡和 MyButton 選項卡。可以使用*代碼背後的*模型添加自定義 .dll 來建立具有其他功能的自定義起始頁,如[將使用者控制項添加到起始頁](../extensibility/adding-user-control-to-the-start-page.md)中所示。 通過將生成的 .vsix 檔發佈到[Visual Studio 應用商店](https://marketplace.visualstudio.com/)網站或其他網站或網路共用,可以與其他使用者共用自定義起始頁。 如需詳細資訊，請參閱 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)。

## <a name="see-also"></a>另請參閱

- [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF 容器控制項](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
