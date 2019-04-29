---
title: 協助工具選項
description: 本文介紹 Visual Studio for Mac 中的協助工具功能及其啟用方式。
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 383f9fb46341eec78fa2daa59bba31dde89ac437
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62985271"
---
# <a name="accessibility"></a>協助工具選項

Visual Studio for Mac 具有下列輔助功能，使具有不同能力的人更容易存取：

- Solution Pad 與 Editor Pad 中的文字放大
- 編輯器中的文字大小選項
- 編輯器中的色彩自訂
- 鍵盤瀏覽
- 快速鍵自訂
- 方法和參數的程式碼完成

除了這些功能外，Apple 還提供數種工具來協助有特殊需求的使用者，例如 VoiceOver 和語音輸入。

如需 macOS 中協助工具功能的詳細資訊，請參閱 [Apple 的網站](https://www.apple.com/accessibility/mac/)。

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中啟用 macOS 輔助技術

根據預設，Visual Studio for Mac 對 macOS 輔助技術的支援處於關閉狀態。 若要啟用它，請依照以下步驟進行：

1. 移至 [Visual Studio] (功能表) > [偏好設定] > [其他] > [協助工具]

2. 檢查 [啟用協助工具] 核取方塊：

   ![[協助工具偏好設定] 核取方塊](media/accessibility-preferences.png)

3. 選取 [重新啟動 Visual Studio] 按鈕以重新啟動 Visual Studio，並啟用對 Apple 輔助技術的支援。

## <a name="how-to-use-keyboard-navigation"></a>HOW TO：使用鍵盤瀏覽

鍵盤瀏覽支援內建於 macOS 中，但為了獲得最全方位的體驗，您應該將 macOS 設定為瀏覽**所有控制項**：

![系統喜好設定鍵盤的所有控制項](media/accessibility-preferences-keyboard.png)

將 [完整鍵盤存取]設定為 [所有控制項]，可讓您瀏覽視窗或對話方塊中的所有控制項。 您接著可以使用下列方式來選取控制項：

- 按 Tab 鍵以向前瀏覽控制項
- 按 Shift-Tab 鍵以向後瀏覽控制項
- 按方向鍵可依箭頭方向在控制項之間移動
- Control-Tab 超出文字區域方塊
- 按空格鍵可啟動目前焦點所在的控制項。

## <a name="how-to-enable-and-use-voiceover"></a>HOW TO：啟用及使用 VoiceOver

若要啟用或停用 VoiceOver，請按 **&#8984; + F5**

VoiceOver 命令在本指南中顯示為 **VO+*key***，其中 **VO** 指的是 [VoiceOver 公用程式] 應用程式中設定的輔助按鍵。 預設輔助按鍵為 **Ctrl + Alt**。例如，根據您的 VoiceOver 輔助按鍵，**VO + M** 將表示 **Ctrl + Alt + M**。為求簡潔，方向鍵將會稱為**左**和**右**，依此類推。

若要瀏覽 Visual Studio for Mac 使用者介面，請使用下列組合鍵：

- **VO + 右 / 左**：在使用者介面項目之間巡覽
    - VoiceOver 將會宣布控制項的標籤和類型，並解釋如何與它進行互動。
- **VO + Shift + 下 / 上**：進入 / 退出項目
    - 進入項目後，您可以使用 **VO + 左 / 右**來巡覽其內的項目。
- **VO + 空格鍵**：選取控制項 / 與控制項互動
- **VO + M**：與 Visual Studio for Mac 功能表列互動

如需使用 VoiceOver 和命令完整清單的詳細資訊，請參閱下列指南：

- [Apple VoiceOver 入門指南](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web)
- [macOS 中的 VoiceOver 命令](http://lab.dotjay.com/notes/voiceover-commands/) \(英文\)

## <a name="see-also"></a>另請參閱

- [Visual Studio (Windows) 的協助工具功能](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
