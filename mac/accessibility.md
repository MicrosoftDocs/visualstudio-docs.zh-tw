---
title: 協助工具選項
description: 本文介紹 Visual Studio for Mac 中的協助工具功能及其啟用方式。
author: conceptdev
ms.author: crdun
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: f90f5fca9d68ed00162fd746ddf291343c8d51f7
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296332"
---
# <a name="accessibility"></a>協助工具選項

除了 macOS 中的功能和公用程式之外，Visual Studio for Mac 具有下列功能，可讓身心障礙人士更方便存取：

- Solution Pad 與 Editor Pad 中的文字放大
- 編輯器中的文字大小選項
- 編輯器中的色彩自訂
- 鍵盤快速鍵自訂
- 方法和參數的程式碼完成

如需 macOS 中協助工具功能的詳細資訊，請參閱 [Apple 的網站](https://www.apple.com/accessibility/mac/)。

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中使用協助工具功能

Visual Studio for Mac 中的協助工具功能預設為關閉。 若要啟用，請遵循下列步驟：

1. 移至 [Visual Studio] > [偏好設定] > [其他] > [協助工具]。

2. 如下圖所示，選取 [啟用協助工具] 核取方塊：

    ![啟用協助工具核取方塊](media/accessibility-image1.png)

3. 按 [重新啟動 Visual Studio] 按鈕，讓協助工具功能生效。

或者，您可以使用命令列來啟用協助工具功能。 做法是在終端機中輸入下列命令：

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

開啟協助工具功能之後，需要重新啟動 Visual Studio。

## <a name="how-to-use-keyboard-navigation"></a>如何：使用鍵盤巡覽

若要啟用鍵盤巡覽，請將 [系統偏好設定] > [鍵盤] > [快速鍵] 中的 [完整鍵盤存取] 選項設定為 [所有控制項]：

![macos 中的系統偏好設定面板](media/accessibility-image2.png)

設定完整鍵盤存取可開啟焦點矩形。 您接著可以使用下列方式來選取控制項：

- 按 Tab 鍵以向前瀏覽控制項
- 按 Shift-Tab 鍵以向後瀏覽控制項
- 按方向鍵可依箭頭方向在控制項之間移動。

按空格鍵可啟動焦點所在的控制項。

## <a name="how-to-enable-and-use-voice-over"></a>如何：啟用及使用 VoiceOver

按 **Cmd + F5** 可開啟或關閉 VoiceOver

若要在 UI VoiceOver 命令之間巡覽，請使用下列命令：

- 在控制項之間移動 VoiceOver 游標：**Ctrl + Alt + 向左鍵 / 向右鍵**

   VoiceOver 會唸出控制項的名稱、相關的詳細資訊，以及可達成的功能。

- 輸入群組和控制項 (像是 Solution Pad、工具箱和其他 Pad)：**Ctrl + Alt + Shift + 向下鍵**

   移至控制項內部之後，可以使用 **Ctrl + Alt + 方向鍵** 在控制項內部中移動。

如需在 macOS 中使用 VoiceOver 的一般資訊，請參閱下列指南：

- [VoiceOver 入門](https://help.apple.com/voiceover/info/guide/10.12/)
- [macOS 中的 VoiceOver 命令](http://lab.dotjay.com/notes/voiceover-commands/) \(英文\)

## <a name="see-also"></a>另請參閱

- [Visual Studio (Windows) 的協助工具功能](/visualstudio/ide/reference/accessibility-features-of-visual-studio)