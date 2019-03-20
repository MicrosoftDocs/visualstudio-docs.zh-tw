---
title: 在 Blend 中修改物件的樣式 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d488149302e21f6e46f1c20a32fb7aecefe8337
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "57869298"
---
# <a name="modify-the-style-of-objects-in-blend"></a>在 Blend 中修改物件的樣式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要自訂物件，最簡單的方式就是在 [屬性] 窗格中設定屬性。  
  
 如果您要重複使用設定或多組設定，請建立可重複使用的資源。 這可以是「樣式」、「範本」，或一些簡單項目，例如自訂色彩。 您也可以依控制項的狀態讓控制項以不同的方式出現。 例如，按鈕會在使用者按一下時變成綠色。  
  
 **本主題內容**：  
  
-   [筆刷：修改物件的外觀](#Brushes)  
  
-   [樣式和範本：跨控制項建立一致的外觀與風格](#Styles)  
  
-   [視覺狀態：依控制項的狀態變更其外觀](#Visual)  
  
-   [資源：建立色彩、樣式和範本，之後重複使用這些項目](#Resources)  
  
##  <a name="Brushes"></a> 筆刷：修改物件的外觀  
 如果您要變更筆刷的外觀，請將筆刷套用至物件。  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Brushes Editor](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor) (筆刷編輯器)。  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>在物件上繪製重複影像或圖樣  
 使用「拼貼筆刷」在物件上繪製重複影像或圖樣。  
  
 若要建立拼貼筆刷，請先建立「影像筆刷」、「繪圖筆刷」或「視覺筆刷」資源。  
  
 使用影像來建立影像筆刷。 下列圖例顯示影像筆刷、並排的影像筆刷和翻轉的影像筆刷。  
  
 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 使用向量繪圖 (例如路徑或圖形) 來建立繪圖筆刷。 下列圖例顯示繪圖筆刷、並排的繪圖筆刷和翻轉的繪圖筆刷。  
  
 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")  
  
 從按鈕等控制項建立視覺筆刷。 下列圖例顯示視覺筆刷和並排的視覺筆刷。  
  
 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tile Brushes](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes) (拼貼筆刷)。  
  
##  <a name="Styles"></a> 樣式和範本：跨控制項建立一致的外觀與風格  
 您可以設計控制項的外觀和行為一次，並將該設計套用至其他控制項，如此就不必一一維護它們。  
  
 **您應該使用樣式嗎？**：如果您只要設定預設屬性 (例如按鈕的色彩)，請使用「樣式」。 您可以修改控制項，即使在套用樣式後也行。  
  
 **您應該使用範本嗎？**：如果您要變更控制項的結構，請使用「範本」。 想像一下將圖形或標誌轉換成按鈕。 在將範本套用至控制項之後，便無法修改控制項。  
  
### <a name="create-a-template-or-style"></a>建立範本或樣式  
 共有兩種方式可以建立範本。 您可以將畫板上的任何物件轉換成控制項，或可以讓範本以現有的控制項為基礎。  
  
 若要將任何物件轉換成控制項範本，請選取該物件，然後在 [工具] 功能表上選擇 [變成控制項]。  
  
 如果您要讓範本以現有控制項為基礎，請選取畫板上的物件。 然後，在畫板上方選擇階層連結按鈕，接著選擇 [編輯範本]，然後選擇 [編輯複本] 或 [建立空的]。  
  
 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 若要建立樣式，請選取物件，接著在 [物件] 功能表中選擇 [編輯樣式]，然後選擇 [編輯複本] 或 [建立空的]。  
  
- 選擇 [編輯複本] 以依照控制項的預設樣式或範本開始著手。  
  
- 選擇 [建立空的] 從頭開始。  
  
  [編輯目前項目] 選項只會在編輯已建立的樣式或範本時才會出現。 若是仍然使用預設系統範本的控制項，則不會顯示此選項。  
  
  在 [建立樣式資源] 對話方塊中，您可以為樣式或範本命名以便之後使用，或將樣式或範本套用至該類型的所有控制項。  
  
  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
>  您無法為每一個類型的控制項建立樣式或範本。 如果控制項不支援此項，階層連結按鈕就不會出現在畫板上。  
>   
>  若要回到主文件的編輯範圍，請按一下 [將範圍傳回] ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b")。  
>   
>  ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create a style](https://www.youtube.com/watch?v=W8YdXDPeKdc) (建立樣式)。  
  
### <a name="apply-a-style-or-template-to-a-control"></a>將樣式或範本套用至控制項  
 在[物件與時間軸](http://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57)面板中以滑鼠右鍵按一下物件，並選擇 [編輯範本]，然後選擇 [套用資源]。  
  
 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>還原控制項的預設樣式或範本  
 選取控制項，然後在[屬性](http://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57)面板中，找出 [樣式] 或 [範本] 屬性。 然後按一下 [進階選項] ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb")，然後按一下捷徑功能表上的 [重設]。  
  
##  <a name="Visual"></a>視覺狀態：依控制項的狀態變更其外觀  
 控制項可根據使用者互動有不同的視覺外觀。 例如，在使用者按一下按鈕時，您可以讓按鈕變成綠色或者執行動畫。 您可以使用轉場來縮短或加長視覺狀態間的時間。  
  
 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Manage the state of your WPF controls](https://www.youtube.com/watch?v=m0PlkF5i6uw) (管理 WPF 控制項的狀態)。  
  
##  <a name="Resources"></a> 資源：建立色彩、樣式和範本，之後重複使用這些項目  
 您可以將專案中幾乎任何項目轉換為資源。 資源只是一個可在應用程式中不同地方重複使用的物件。 例如，您可以建立色彩一次、使它變成資源，然後在數個物件上使用該色彩。 若要變更所有這些物件的色彩，只須變更色彩資源即可。  
  
 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-b153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [A brief touch on resources](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources) (資源的簡短接觸)。  
  
## <a name="see-also"></a>請參閱  
 [使用 Blend for Visual Studio 建立 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
