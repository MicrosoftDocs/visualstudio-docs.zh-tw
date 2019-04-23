---
title: HOW TO：建立基本材質 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a343cb508933b91f5400ff6bc17c285a54bd2e87
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076795"
---
# <a name="how-to-create-a-basic-texture"></a>HOW TO：建立基本紋理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件將示範如何使用影像編輯器來建立基本材質。  
  
 本文件示範下列活動︰  
  
- 設定材質的大小  
  
- 設定前景和背景色彩  
  
- 使用 Alpha 色板 (透明度)  
  
- 使用 [填滿] 和 [橢圓形] 工具  
  
- 設定工具屬性  
  
## <a name="creating-a-basic-texture"></a>建立基本材質  
 您可以使用影像編輯器來建立和修改遊戲或應用程式的紋理和影像。  
  
 下列步驟示範如何建立代表「靶心」目標的材質。當您完成時，材質看起來應該類似下列圖片。 設定影像編輯器使用綠色棋盤式圖樣顯示材質，更能展現出材質中的透明度。  
  
 ![以綠色顯示透明度的「靶心」目標](../designers/media/digit-bullseye-texture-in-editor.png "Digit-Bullseye-Texture-In-Editor")  
  
 開始之前，請確定已顯示 [屬性] 視窗。 您可以在工作時，使用 [屬性] 視窗來設定影像大小、變更工具屬性，以及指定色彩。  
  
#### <a name="to-create-a-bullseye-target-texture"></a>建立「靶心」目標材質  
  
1. 建立要使用的材質。 如需有關如何將材質加到專案的詳細資訊，請參閱[影像編輯器](../designers/image-editor.md)中的＜使用者入門＞一節。  
  
2. 將影像大小設定為 512x512 像素。 在 [屬性] 視窗中，將 [寬度] 和 [高度] 屬性的值設定為 `512`。  
  
3. 在 [影像編輯器] 工具列上，選擇 [填滿] 工具。 [屬性] 視窗現在會將 [填滿] 工具的屬性和影像屬性一起顯示。  
  
4. 將前景色彩設為完全透明的黑色。 在 [屬性] 視窗的 [色彩] 屬性群組中，選取 [前景]。 將色彩選擇器旁邊的 [R]、[G]、[B] 及 [A] 屬性值設定為 `0`。  
  
5. 在 [影像編輯器] 工具列上，選擇 [填滿] 工具，然後按住 Shift 鍵並選擇影像中的任意點。 使用 Shift 鍵會造成填滿色彩的 Alpha 值取代影像中的色彩；否則，Alpha 值是用來將填滿色彩和影像中的色彩混合。  
  
   > [!IMPORTANT]
   >  此步驟加上前一步驟中選取的色彩，可確保會備妥您即將繪製的「靶心」目標材質基底影像。 以透明黑色填滿影像，同時目標邊界為黑色時，目標周圍不會有鋸齒化成品。  
  
6. 在 [影像編輯器] 工具列上，選擇 [橢圓形] 工具。  
  
7. 將前景色彩設為完全不透明的黑色。 將 [R]、[G] 及 [B] 屬性的值設定為 `0`，並將 [A] 屬性的值設定為 `255`。  
  
8. 將背景色彩設為完全不透明的白色。 在 [屬性] 視窗的 [色彩] 屬性群組中，選取 [背景]。 將 [R]、[G]、[B] 及 [A] 屬性的值設定為 `255`。  
  
9. 設定橢圓形外框的寬度。 在 [屬性] 視窗的 [外觀] 屬性群組中，將 [寬度] 屬性的值設定為 `8`。  
  
10. 確定已啟用消除鋸齒功能。 在 [屬性] 視窗的 [外觀] 屬性群組中，確定已設定 [消除鋸齒] 屬性。  
  
11. 使用 [橢圓形] 工具，繪製一個從像素座標 `(3, 3)` 到像素座標 `(508, 508)` 的圓形。 您在繪製時按住 Shift 鍵，可以更輕鬆繪製圓形。  
  
    > [!NOTE]
    >  目前指標位置的像素座標會顯示在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 狀態列。  
  
12. 變更背景色彩。 將 [R] 設定為 `44`、[G] 設為 `165`、[B] 設為 `211`，並將 [A] 設為 `255`。  
  
13. 繪製另一個從像素座標 `(64, 64)` 到像素座標 `(448, 448)` 的圓形。  
  
14. 將背景色彩變更，回到完全不透明的白色。 將 [R]、[G]、[B] 及 [A] 設定為 `255`。  
  
15. 繪製另一個從像素座標 `(128, 128)` 到像素座標 `(384, 384)` 的圓形。  
  
16. 變更背景色彩。 將 [R] 設定為 `255`、[G] 和 [B] 設為 `64`，並將 [A] 設為 `255`。  
  
17. 繪製另一個從像素座標 `(192, 192)` 到像素座標 `(320, 320)` 的圓形。  
  
    完成「靶心」目標材質。 以下是呈現透明度的最終影像。  
  
    ![完整的「靶心」目標材質](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")  
  
    下一步可以產生這個材質的 MIP 層級。 如需相關資訊，請參閱[如何：建立和修改 MIP 層級](../designers/how-to-create-and-modify-mip-levels.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Image Editor](../designers/image-editor.md)
