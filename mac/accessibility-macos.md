---
title: 使用 macOS 協助工具選項
description: 使用 macOS 協助工具選項和功能，例如高對比、鍵盤流覽和 VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998382"
---
# <a name="accessibility-features-of-macos"></a>MacOS 的協助工具功能

macOS 是可存取的作業系統，有許多功能可協助使用者進行不同的能力。 這些功能包括高對比模式、鍵盤導覽和 VoiceOver (macOS 螢幕讀取器) 。

## <a name="enable-accessibility-features"></a>啟用協助工具功能

在 Visual Studio for Mac 中，輔助技術的支援預設為關閉。 啟用協助工具支援：

1. 移至 **Visual Studio (] 功能表)**  >  **喜好** 設定  >  ****，然後選取 [**協助工具**]。

1. 選取 [ **啟用協助工具** ] 核取方塊。

   ![協助工具喜好設定的螢幕擷取畫面，其中已選取 [啟用協助工具]](media/accessibility-preferences.png)

1. 選取 [ **重新開機 Visual Studio** ]，以啟用 Apple 輔助技術的支援。

或者，您可以使用命令列來啟用協助工具功能。 做法是在終端機中輸入下列命令：

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

透過命令列變更此設定之後，您將需要重新開機 Visual Studio。

## <a name="increase-the-contrast-in-macos"></a>增加 macOS 中的對比

Visual Studio for Mac 在 macOS 中支援更高的對比，增加 UI 元素的對比，並讓大綱更明確地定義。 若要啟用：

1. 開啟 [ **系統偏好** 設定]。

1. 移至 [ **協助工具**]，然後選取 [ **顯示**]。

1. 選取 [ **提高對比** ] 核取方塊。
