---
title: 逐步解說：將自訂 XAML 新增至起始頁 |Microsoft Docs
description: 瞭解如何使用本逐步解說來建立包含網頁瀏覽器的自訂 Visual Studio 起始頁。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 47c83906b84263af966737a309de0b5096031f94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926867"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>逐步解說：將自訂 XAML 新增至起始頁

本逐步解說示範如何建立包含網頁瀏覽器的自訂 Visual Studio 起始頁。

## <a name="add-custom-xaml"></a>新增自訂 XAML

1. 遵循 [建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)中的指示，建立起始頁。

2. 在 *MainWindow .xaml* 檔案中，尋找 \<Grid> 區段。

3. 在專案 \<TabControl> 內加入元素和 \<TabItem> \< Grid> ，如下列範例所示。

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. 新增第二個 \<TabItem> ，具有 \<Button> 開啟新專案的元素：

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

     Visual Studio 的實驗實例隨即開啟，並已安裝自訂起始頁，但未選取。

2. 在 Visual Studio 的實驗實例中，開啟 [ **工具/Options]/[環境** ] 頁面。

3. 選取 [ **啟動**]。 在 [ **自訂起始頁** ] 清單中，選取您的 *.xaml* 檔案，然後按一下 **[確定]**。

4. 在 [檢視]  功能表上，按一下 [起始頁] 。

5. 按一下 [ **Bing** ] 索引標籤。

     您應該會看到 Bing 網頁。

6. 按一下 [ **MyButton** ] 索引標籤。

     您應該會看到 [ **MyProject** ] 按鈕，這會開啟 [ **新增專案** ] 對話方塊。

7. 關閉實驗實例。

若要套用自訂起始頁，請在 [**工具**  >  **選項**]  >  **環境** 中選取 [**啟動**]。 在 [ **自訂起始頁** ] 清單中，選取您的 *.xaml* 檔案，然後按一下 **[確定]**。

## <a name="next-steps"></a>下一步

[Visual Studio 開始] 頁面現在包含一個索引標籤，可顯示網頁瀏覽器索引標籤和 [MyButton] 索引標籤。您可以使用程式 *代碼後端* 模型加入自訂 .dll，以建立具有其他功能的自訂起始頁，如 [將使用者控制項新增至起始頁](../extensibility/adding-user-control-to-the-start-page.md)所示。 您可以將產生的 .vsix 檔案發佈至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 網站或另一個網站或網路共用，以與其他使用者共用自訂起始頁。 如需詳細資訊，請參閱 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)。

## <a name="see-also"></a>另請參閱

- [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF 容器控制項](/previous-versions/bb675291(v=vs.110))