---
title: 修改物件的樣式
titleSuffix: Blend for Visual Studio
description: 瞭解如何藉由套用筆刷、設定視覺狀態以及套用可重複使用的樣式和範本，在 Blend for Visual Studio 中修改物件的樣式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2b98f814e1f310c7d7f281457589a1a9f7d21653
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966548"
---
# <a name="modify-the-style-of-objects-in-blend-for-visual-studio"></a>在 Blend for Visual Studio 中修改物件的樣式

若要自訂物件，最簡單的方式就是在 [屬性] 窗格中設定屬性。

如果您想要重複使用設定或多組設定，請建立可重複使用的資源。 這可以是「樣式」、「範本」，或一些簡單項目，例如自訂色彩。 您也可以依控制項的狀態讓控制項以不同的方式出現。 例如，按鈕會在使用者按一下時變成綠色。

## <a name="brushes-modify-the-appearance-of-an-object"></a>筆刷：修改物件的外觀

如果您要變更筆刷的外觀，請將筆刷套用至物件。

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>在物件上繪製重複影像或圖樣

使用「拼貼筆刷」在物件上繪製重複影像或圖樣。

若要建立拼貼筆刷，請先建立「影像筆刷」、「繪圖筆刷」或「視覺筆刷」資源。

使用影像來建立影像筆刷。 下列圖例顯示影像筆刷、並排的影像筆刷和翻轉的影像筆刷。

![影像筆刷](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![並排顯示的影像筆刷](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![翻轉的影像筆刷](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

使用向量繪圖 (例如路徑或圖形) 來建立繪圖筆刷。 下列圖例顯示繪圖筆刷、並排的繪圖筆刷和翻轉的繪圖筆刷。

![繪圖筆刷](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![並排顯示的繪圖筆刷](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![翻轉的繪圖筆刷](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

從按鈕等控制項建立視覺筆刷。 下列圖例顯示視覺筆刷和並排的視覺筆刷。

![視覺筆刷](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![並排顯示的視覺筆刷](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>樣式和範本：跨控制項建立一致的外觀與風格

您可以設計控制項的外觀和行為一次，並將該設計套用至其他控制項，如此就不必一一維護它們。

**您應該使用樣式嗎？**：如果您只要設定預設屬性 (例如按鈕的色彩)，請使用「樣式」。 您可以修改控制項，即使在套用樣式後也行。

**您應該使用範本嗎？**：如果您要變更控制項的結構，請使用「範本」。 想像一下將圖形或標誌轉換成按鈕。 在將範本套用至控制項之後，便無法修改控制項。

### <a name="create-a-template-or-style"></a>建立範本或樣式

共有兩種方式可以建立範本。 您可以將畫板上的任何物件轉換成控制項，或可以讓範本以現有的控制項為基礎。

若要將任何物件轉換成控制項範本，請選取該物件，然後在 [工具] 功能表上選擇 [變成控制項]。

如果您要讓範本以現有控制項為基礎，請選取畫板上的物件。 然後，在畫板上方選擇階層連結按鈕，接著選擇 [編輯範本]，然後選擇 [編輯複本] 或 [建立空的]。

![[編輯範本] 功能表](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

若要建立樣式，請選取物件，接著在 [物件] 功能表中選擇 [編輯樣式]，然後選擇 [編輯複本] 或 [建立空的]。

- 選擇 [編輯複本] 以依照控制項的預設樣式或範本開始著手。

- 選擇 [建立空的] 從頭開始。

[編輯目前項目] 選項只會在編輯已建立的樣式或範本時才會出現。 若是仍然使用預設系統範本的控制項，則不會顯示此選項。

在 [建立樣式資源] 對話方塊中，您可以為樣式或範本命名以便之後使用，或將樣式或範本套用至該類型的所有控制項。

![[建立樣式資源] 對話方塊](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> 您無法為每一個類型的控制項建立樣式或範本。 如果控制項不支援此項，階層連結按鈕就不會出現在畫板上。
> 若要回到主文件的編輯範圍，請按一下 [將範圍傳回] ![將範圍傳回圖示](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png)。

### <a name="apply-a-style-or-template-to-a-control"></a>將樣式或範本套用至控制項

在 [[物件與時間軸]](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) 視窗中以滑鼠右鍵按一下物件，選擇 [編輯範本]，然後選擇 [套用資源]。

![[套用資源] 功能表](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>還原控制項的預設樣式或範本

選取控制項，然後在 [屬性] 視窗中，找出 [ **樣式** ] 或 [ **範本** ] 屬性。 選擇 [進階選項]，然後按一下捷徑功能表上的 [重設]。

## <a name="visual-states"></a>視覺狀態

視覺狀態可讓您依控制項的狀態變更其外觀。 控制項可根據使用者互動有不同的視覺外觀。 例如，您可以讓按鈕在使用者按一下它時變成綠色，或是執行動畫。 使用轉換來縮短或加長視覺狀態間的時間。

![滑鼠移至上方狀態](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**觀看短片：** ![播放按鈕](../designers/media/bldadminconsoleinitialconfigicon.PNG) [管理 WPF 控制項的狀態](https://www.youtube.com/watch?v=m0PlkF5i6uw) \(英文\)。

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>資源：建立色彩、樣式和範本，之後重複使用這些項目

您可以將專案中幾乎任何項目轉換為資源。 資源只是一個可在應用程式中不同地方重複使用的物件。 例如，您可以建立色彩一次、使它變成資源，然後在數個物件上使用該色彩。 若要變更所有這些物件的色彩，只須變更色彩資源即可。

![[將色彩轉換為資源] 按鈕](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![[建立色彩資源] 對話方塊](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>另請參閱

- [使用 Blend for Visual Studio 建立 UI](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
