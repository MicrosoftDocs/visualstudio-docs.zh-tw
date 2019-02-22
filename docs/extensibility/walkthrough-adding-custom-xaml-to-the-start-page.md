---
title: 逐步解說：[開始] 頁面中加入自訂的 XAML |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a828fe6f7944e2bb0d9527d781c66630ed1f3879
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947279"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>逐步解說：將自訂的 XAML 加入至 [開始] 頁面
本逐步解說示範如何建立自訂 Visual Studio 起始頁包含網頁瀏覽器。  
  
## <a name="adding-custom-xaml"></a>新增自訂的 XAML  
  
1.  依照中的指示，建立起始頁[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)。  
  
2.  在  *MainWindow.xaml*檔案中，尋找\<方格 > 一節。  
  
3.  新增\<TabControl > 項目和\<TabItem > 內\<方格 > 項目，如下列範例所示。  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  新增第二\<TabItem >，使用\<按鈕 > 項目，開啟新的專案：  
  
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
  
## <a name="testing-the-custom-start-page"></a>測試自訂起始頁  
  
1.  請按 **F5**。  
  
     Visual Studio 的實驗執行個體隨即開啟，並自訂起始頁已安裝但不是選取。  
  
2.  在 Visual Studio 的實驗性執行個體，開啟**工具 /Options / 環境**頁面。  
  
3.  選取 **啟動**。 在 **自訂起始頁**清單中，選取您 *.xaml*檔案，然後按一下**確定**。  
  
4.  在 [檢視]  功能表上，按一下 [起始頁] 。  
  
5.  按一下 [ **Bing** ] 索引標籤。  
  
     您應該會看到 Bing 網頁。  
  
6.  按一下 [ **MyButton** ] 索引標籤。  
  
     您應該會看到**MyProject**按鈕，這會開啟**新的專案**對話方塊。  
  
7.  關閉實驗執行個體。  
  
## <a name="apply-the-custom-start-page"></a>套用自訂起始頁  
  
### <a name="to-test-the-custom-start-page"></a>若要測試自訂起始頁  
  
1.  在 **工具 / 選項 / 環境**，選取**啟動**。 在 **自訂起始頁**清單中，選取您 *.xaml*檔案，然後按一下**確定**。  
  
## <a name="next-steps"></a>後續步驟  
 Visual Studio 起始頁現在包含網頁瀏覽器索引標籤和 MyButton 索引標籤會顯示索引標籤。您可以建立自訂啟動使用具有其他功能頁面*程式碼後置*模型中所示，新增自訂.dll[新增至 [入門] 頁面的使用者控制項](../extensibility/adding-user-control-to-the-start-page.md)。 您也可以發行至產生的.vsix 檔案與其他使用者共用自訂起始頁[Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，或以另一個網站或網路共用。 如需詳細資訊，請參閱 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF 控制項](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)