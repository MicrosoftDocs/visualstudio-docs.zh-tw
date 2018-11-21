---
title: 原始檔編輯器
description: 使用 Visual Studio for Mac 中的原始檔編輯器
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: b284cde511b17863861908d9967bbea7672e297b
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295692"
---
# <a name="source-editor"></a>原始檔編輯器

可靠的原始檔編輯器是以簡潔且具效率的方式撰寫程式碼的必要項目。 Visual Studio for Mac 提供一個精細的原始檔編輯器，其為您與 IDE 互動的核心。 原始檔編輯器提供您可能預期以及可輕鬆執行工作所需的功能：範圍從基礎功能 (例如語法反白顯示、程式碼片段和程式碼摺疊功能) 到其 Roslyn 編譯器整合的優點 (例如功能完整的 IntelliSense 程式碼完成)。

Visual Studio for Mac 中的原始檔編輯器允許能存取 IDE 中所有其他功能 (例如偵錯、重構和版本控制整合) 的順暢體驗。

本文章介紹原始檔編輯器的一些主要功能，並且探索如何以最具生產力的方式使用 Visual Studio for Mac。

## <a name="the-source-editor-experience"></a>原始檔編輯器體驗

在整個程式碼中有效率地檢視和移動是開發工作流程中不可或缺的部分。 決定如何檢視和維護程式碼是個人決策，而且不同的開發人員會不同，並且不同的專案通常也會不同。

Visual Studio for Mac 提供許多功能強大的功能，讓跨平台開發更容易進行且更具可用性。 下列各節描述一些重點。

## <a name="code-folding"></a>程式碼摺疊功能

程式碼摺疊功能可讓您輕鬆地管理大型原始程式碼檔，方法是允許開發人員顯示或隱藏完整程式碼區段，例如 using 指示詞、未定案程式碼和註解，以及 #region 陳述式。 程式碼摺疊功能在 Visual Studio for Mac 中預設會關閉

若要開啟程式碼摺疊功能，請巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [一般] > [程式碼摺疊功能]：

![程式碼摺疊功能選項](media/source-editor-image1.png)

此功能表預設也會包含摺疊 #regions 和註解的選項，並顯示具名提示，而非程式碼。

若要顯示或隱藏各區段，請使用行號旁的公開揭示小工具：

![顯示或隱藏程式碼中的各節](media/source-editor-image2.png)

使用 [檢視] > [摺疊] > [切換摺疊]/[切換所有摺疊] 功能表項目，也可以切換摺疊的顯示和隱藏：

![摺疊功能表項目](media/source-editor-image19.png)

此功能表項目也可以用來啟用或停用程式碼摺疊功能。

## <a name="white-space"></a>空白字元

您可能需要檢視原始程式碼中的不可見字元。 這是能確保您符合編碼標準且不會浪費空間的可見方法。 此方法在撰寫 F# 時也十分有用，因為撰寫 F# 需仰賴針對評估程式碼的精確縮排行。

巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [標記與尺規]，來設定顯示空白的選項。 選取此選項允許設定將顯示不可見字元的「時機」 ：[永不]、[選取時] 或 [一律]：

![顯示不可見字元選項](media/source-editor-image3.png)

也會提供顯示定位點、空格和行尾結束符號的選項：

![顯示索引標籤和空格](media/source-editor-image4.png)

不可見字元會顯示為灰色點，如下圖所示：

![顯示的空白字元](media/source-editor-image22.png)

## <a name="ruler"></a>尺規

資料行尺規適用於判斷行長度，特別是處理具有行長度指導方針的小組時。 巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [標記與尺規]，並選取 (或取消選取) [顯示資料行尺規]，即可開啟或關閉資料行尺規，如下圖所示：

![醒目提示 [顯示資料行尺規] 的 [喜好設定] 對話方塊](media/source-editor-image5.png)

 這會顯示為原始檔編輯器中的淺灰色垂直線。

## <a name="highlight-identifier-references"></a>反白顯示識別碼參考 (Highlight identifier references)

開啟 [反白顯示識別碼參考] 選項時，您可以選取原始程式碼中的任何符號，而原始檔編輯器將會針對該檔案中所有其他參考提供視覺效果指南。 若要開啟此選項，請移至 [Visual Studio] > [喜好設定] > [文字編輯器] > [標記與尺規]，並選取 [醒目提示識別碼參考]，如下圖所示：

![醒目提示 [醒目提示識別碼參考] 的 [喜好設定] 對話方塊](media/source-editor-image6.png)

反白顯示的色彩也適用於表示要指派或參考的項目。 如果指派某個項目，則會以紅色將它反白顯示；如果參考它，則會以藍色反白顯示：

![顯示醒目提示色彩的範例](media/source-editor-image7.png)

## <a name="see-also"></a>另請參閱

- [程式碼編輯器的功能 (Windows 上的 Visual Studio)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [大綱 (Windows 上的 Visual Studio)](/visualstudio/ide/outlining)