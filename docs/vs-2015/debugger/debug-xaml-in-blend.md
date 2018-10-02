---
title: 在 Blend 中的 XAML 進行偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1fe1c312c747e25fc1b1e93a51e26d6e67c4a9b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498762"
---
# <a name="debug-xaml-in-blend"></a>在 Blend 中偵錯 XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[在 Blend 中的偵錯 XAML](https://docs.microsoft.com/visualstudio/debugger/debug-xaml-in-blend)。  
  
您可以使用 [!INCLUDE[blend_first](../includes/blend-first-md.md)] 中的工具為應用程式的 XAML 偵錯。 當您建置專案時，任何錯誤都會顯示在**結果**面板。 只要按兩下錯誤，即可找到與該錯誤相關的標記。 如果您需要更多工作空間，您可以隱藏**結果**按 F12 的面板。  
  
## <a name="syntax-errors"></a>語法錯誤  
 如果 XAML 或程式碼後置檔案不符合語言的格式規則，就會發生語法錯誤。 錯誤描述有助於您了解修正方法。 這份清單也會指出發生錯誤的檔案名稱與行號。 XAML 錯誤會顯示在**標記**索引標籤中**結果**面板。  
  
> [!TIP]
>  XAML 是 XML 架構的標記語言，並且遵循 XML 語法規則。  
  
 常見的一些 XAML 語法錯誤原因如下：  
  
-   關鍵字拼錯或大小寫錯誤。  
  
-   屬性或文字字串周圍遺漏引號。  
  
-   XAML 元素遺漏結尾標。  
  
-   XAML 元素位於禁止的位置。  
  
 如需有關一般 XAML 語法的詳細資訊，請參閱 <<c0> [ 基本 XAML 語法指南](http://go.microsoft.com/fwlink/?LinkId=329942)。  
  
 此外，您也可以在 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] 中辨識並解決簡單的程式碼後置語法錯誤、編譯錯誤和執行階段錯誤。 但是，在 Visual Studio 中能夠較容易辨識並解決程式碼後置語法錯誤。  
  
### <a name="debugging-sample-xaml-code"></a>偵錯範例 XAML 程式碼  
 下列範例會引導您在 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] 中完成簡單的 XAML 偵錯工作階段。  
  
##### <a name="to-create-a-project"></a>若要建立專案  
  
1.  在  [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]，開啟**檔案**功能表，然後再按一下**新專案**。  
  
     在 [**新的專案**] 對話方塊中，專案類型清單隨即出現在左邊。 當您按一下專案類型時，與該類型有關聯的專案範本會顯示在右邊。  
  
2.  在專案類型清單中，按一下**XAML （Windows 市集）**。  
  
3.  在專案範本清單中，按一下**空白應用程式**。  
  
4.  在 **名稱**文字方塊中，輸入`DebuggingSample`。  
  
5.  在 **位置**文字中，確認專案的位置。  
  
6.  在 **語言**清單中，按一下**Visual C#**，然後按一下  **確定**建立專案。  
  
7.  以滑鼠右鍵按一下設計介面上，按一下 再**檢視原始檔**切換至**分割**檢視。  
  
8.  複製下列程式碼，即可**複製**右上角的 程式碼連結。  
  
    ```  
    <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
         <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
    </Grid>  
  
    ```  
  
9. 找出預設值**方格**，並貼上的程式碼的開頭和結尾之間**格線**標記。 當您完成時，您的程式碼應該像這樣：  
  
    ```  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
  
    ```  
  
10. 按 Ctrl+Shift+B 建置專案。  
  
 出現錯誤訊息，告訴您無法建置專案，而**結果**面板列出發生的錯誤會出現在底部的 應用程式。  
  
 ![偵錯 Blend for Visual Studio 中的 XAML](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>解決 XAML 錯誤  
 偵測到 XAML 錯誤時，設計介面上會出現警示，說明您的專案包含無效的標記。 當您解決錯誤，錯誤清單中**結果**面板會進行更新。 當您解決所有錯誤時，設計介面會再次出現並顯示應用程式畫面。  
  
##### <a name="to-resolve-the-xaml-errors"></a>若要解決 XAML 錯誤  
  
1.  按兩下清單中的第一個錯誤。 這個錯誤的描述是「值 '<' 不是有效的屬性」。 當您按兩下錯誤時，指標隨即找到程式碼中對應的位置。 `<` 前面的 `Button` 為有效字元，並非錯誤訊息中建議的屬性。 如果查看前一行程式碼，您會注意到 `Top` 屬性的右引號不見了。 請輸入右引號。 請注意，清單中的錯誤**結果**面板更新以反映您的變更。  
  
2.  按兩下描述"'0' 無效的名稱開頭。 」 `Margin="0,149,0,0"` 格式正確，會出現。 但是，請注意 `Margin` 的色彩標示與程式碼中的其他 `Margin` 執行個體不符。 由於這個 `VerticalAlignment="Top` 前方的名稱/值組少了右引號 (`Margin="`)，因此就被視為屬於前一個屬性的值，導致 0 被視為名稱/值組的開頭。 請輸入 `Top` 的右引號。 中的錯誤清單**結果**面板更新以反映您的變更。  
  
3.  按兩下剩餘的錯誤 [關閉的 XML 標籤 "Button" 不相符]。 滑鼠指標位於右**格線**標記 (`</Grid>`)，建議的錯誤位於`Grid`物件。 請注意，第二個 `Button` 物件少了結尾標記。 您加入結尾之後`/`，則**結果**面板清單也會更新。 我們現在已經解決一開始出現的錯誤，但是又出現了兩個錯誤。  
  
4.  按兩下 [無法識別或無法存取成員 "content"。]， `c` 中的 `content` 應該是大寫才對。 請將小寫 "c" 改成大寫 "C"。  
  
5.  按兩下 「 屬性 'Mame' 不存在於 'http://schemas.microsoft.com/winfx/2006/xaml' 命名空間。 」 "Mame" 中的 "M" 應該是 "N" 才對。 請將 "M" 改成 "N"。 現在已經可以解析 XAML，應用程式也隨即顯示在設計介面上。  
  
     ![偵錯 Blend for Visual Studio 中的 XAML](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
     按 Ctrl+Shift+B 建置專案，確定不再發生其他任何錯誤。  
  
## <a name="debugging-in-visual-studio"></a>Visual Studio 偵錯  
 您可以在 Visual Studio 中開啟 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] 專案，讓應用程式的程式碼偵錯更為容易。 若要開啟 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]在 Visual Studio 專案中，以滑鼠右鍵按一下中的專案**專案**] 面板，然後按一下 [ **Visual Studio 中編輯**。 在 Visual Studio 中結束偵錯工作階段之後，請按 Ctrl+Shift+S 儲存所有變更，然後再切換回 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]。 此時會出現要您重新載入專案的提示畫面。 按一下 **全部**以繼續使用[!INCLUDE[blend_subs](../includes/blend-subs-md.md)]。  
  
 如需有關偵錯您的應用程式的詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的偵錯 Windows 市集應用程式](http://go.microsoft.com/fwlink/?LinkId=329944)。  
  
## <a name="getting-help"></a>取得協助  
 如果您需要偵錯的詳細說明您[!INCLUDE[blend_subs](../includes/blend-subs-md.md)]應用程式中，您可以搜尋[Windows 市集應用程式社群論壇](http://go.microsoft.com/fwlink/?LinkId=280308)針對與您問題相關的文章或張貼問題。



