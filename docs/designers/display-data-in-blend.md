---
title: "在 Blend 中顯示資料 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1097a5724e1fcab96be99c58532e15fedd59da30
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="display-data-in-blend"></a>在 Blend 中顯示資料
您可以在自訂頁面的版面配置時於設計工具中檢視範例資料。 您可以從頭產生範例資料，或使用現有的類別。 您也可以連接到在執行應用程式時會出現於其中的 *「即時資料」* (Live data)。  
  
 **本主題內容：**  
  
-   [產生範例資料](#Scratch)  
  
-   [從類別產生範例資料](#Existing)  
  
-   [在 WPF 應用程式中顯示即時資料](#LiveWPF)  
  
-   [在市集或 Phone 應用程式中顯示即時資料](#LiveStore)  
  
##  <a name="Scratch"></a> 產生範例資料  
 若要產生範例資料，請開啟 XAML 文件。 在 [資料]  面板中，選擇 [建立範例資料] ![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") 按鈕，然後選擇 [新增範例資料] 。  
  
 在 [資料]  面板中定義資料結構，然後將它繫結至任何頁面上的 UI 項目。  
  
 ![](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png "496d7ebc-fe46-42f6-95a8-57b0e5be5d49")  
  
 如果您希望範例資料在執行應用程式時出現在頁面中，請選擇 [資料來源選項]  ![](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png "ae1fd260-4f84-420d-b196-45fde357d81d")，然後選擇 [執行應用程式時啟用] 。  
  
 ![](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png "05d5356d-91bb-4e6b-b3f7-29b76852c4b3")  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create sample data from scratch](http://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2) (從頭開始建立範例資料)。  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Mixing up some data binding with Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg) (與 Blend 混合一些資料繫結)。  
  
##  <a name="Existing"></a> 從類別產生範例資料  
 如果您已經建立可描述資料結構的類別，可以從中產生範例資料。  
  
 若要從類別產生範例資料，請開啟 XAML 文件，然後在 [資料]  面板中，按一下 [建立範例資料] ![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") 按鈕，然後按一下 [從類別建立範例資料] 。  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create sample data from a class](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=video&cd=1&cad=rja&uact=8&ved=0CB0QtwIwAA&url=http%3A%2F%2Fchannel9.msdn.com%2FShows%2FInside%2BWindows%2BPhone%2FIWP54--Windows-Phone-Data-Binding-and-the-Magic-of-XAML&ei=F1oHVNryM4ysogSJ2oDYDw&usg=AFQjCNEYvw1WA1rdF7bfpj5RwMLUs7RCVg) (從類別建立範例資料)。  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Mixing up some data binding with Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg) (與 Blend 混合一些資料繫結)。  
  
##  <a name="LiveWPF"></a> 在 WPF 應用程式中顯示即時資料  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create an object data source](http://www.bing.com/videos/watch/video/using-an-objectdatasource-in-expression-blend/qmavx0xg) (建立物件資料來源)。  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create an XML data source](https://www.youtube.com/watch?v=RjQueappjqk&feature=youtube_gdata) (建立 XML 資料來源)。  
  
##  <a name="LiveStore"></a> 在市集或 Phone 應用程式中顯示即時資料  
 請參閱 [使用資料和檔案 (XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/br229562.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Blend for Visual Studio 建立 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)