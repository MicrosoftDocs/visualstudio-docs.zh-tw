---
title: "原始檔編輯器 | Microsoft Docs"
description: "使用 Visual Studio for Mac 中的原始檔編輯器"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: f52e60c0ade8cebc78b3408b4ef81ef85fcd767b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="source-editor"></a>原始檔編輯器

可靠的原始檔編輯器是以簡潔且具效率的方式撰寫程式碼的必要項目。 Visual Studio for Mac 提供一個精細的原始檔編輯器，其為您與 IDE 互動的核心。 原始檔編輯器提供您可能預期以及可輕鬆執行工作所需的功能：範圍從基礎功能 (例如語法反白顯示、程式碼片段和程式碼摺疊功能) 到其 Roslyn 編譯器整合的優點 (例如功能完整的 IntelliSense 程式碼完成)。

Visual Studio for Mac 中的原始檔編輯器允許 IDE 所提供的所有其他功能 (例如偵錯、重構和版本控制整合) 的順暢體驗。

本主題介紹原始檔編輯器的一些主要功能，並且探索如何以最具生產力的方式使用 Visual Studio for Mac。

## <a name="the-source-editor-experience"></a>原始檔編輯器體驗

在整個程式碼中有效率地檢視和移動是開發工作流程中不可或缺的部分。 決定如何檢視和維護程式碼是個人決策，而且不同的開發人員會不同，並且不同的專案通常也會不同。

Visual Studio for Mac 提供許多功能強大的功能，讓跨平台開發更容易進行且更具可用性。 下列各節描述一些重點。


### <a name="code-folding"></a>程式碼摺疊功能

程式碼摺疊功能可讓您輕鬆地管理大型原始程式碼檔，方法是允許開發人員顯示或隱藏完整程式碼區段，例如 using 指示詞、未定案程式碼和註解，以及 #region 陳述式。 這在 Visual Studio for Mac 中預設會予以關閉

若要開啟程式碼摺疊功能，請巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [一般] > [程式碼摺疊功能]:

![程式碼摺疊功能選項](media/source-editor-image1.png)

除了提供啟用程式碼摺疊功能的選項之外，這個功能表預設也會包含摺疊 #regions 和註解的選項，並顯示具名提示，而非程式碼。

若要顯示或隱藏各區段，請使用行號旁的公開揭示小工具：

 ![顯示或隱藏程式碼中的各節](media/source-editor-image2.png)

使用 [檢視] > [摺疊] > [切換摺疊]/[切換所有摺疊] 功能表項目，也可以切換摺疊的顯示和隱藏：

 ![摺疊功能表項目](media/source-editor-image19.png)

此功能表項目也可以用來啟用或停用程式碼摺疊功能。

### <a name="white-space"></a>空白字元

您可能需要可以檢視原始程式碼中的不可見字元。 明顯可見，這確保您符合編碼標準，而且不一定會浪費空間。 撰寫 F# 時，它也十分有用，而這取決於評估程式碼的精確縮排行。

巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [標記與尺規]，來設定顯示空白的選項，如下所示。 選取此選項允許設定將顯示不可見字元的「時機」：[永不]、[選取時] 或 [一律]：

 ![顯示不可見字元選項](media/source-editor-image3.png)

也會提供顯示定位點、空格和行尾結束符號的選項：

 ![顯示索引標籤和空格](media/source-editor-image4.png)

 不可見字元會顯示為灰色點，如下所示：

 ![顯示的空白字元](media/source-editor-image22.png)


### <a name="ruler"></a>尺規

顯示資料行尺規適用於判斷行長度，特別是處理具有行長度指導方針的小組時。 巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [標記與尺規]，並選取 (或取消選取) [Show Column ruler] (顯示資料行尺規)，即可開啟或關閉資料行尺規，如下所示：

 ![](media/source-editor-image5.png)

 這會顯示為原始檔編輯器中的淺灰色垂直線。


### <a name="highlight-identifier-references"></a>反白顯示識別碼參考 (Highlight identifier references)

開啟這個選項時，開發人員可以將滑鼠游標放在原始程式碼的任何符號上方，而原始檔編輯器將會提供該檔案中所有其他參考的視覺效果指南。 巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [標記與尺規]，並選取 [Highlight identifier references] (反白顯示識別碼參考)，即可開啟此項目，如下所示：

![](media/source-editor-image6.png)

反白顯示的色彩也適用於表示要指派或參考的項目。 如果指派某個項目，則會以紅色將它反白顯示；如果參考它，則會以藍色反白顯示：

![](media/source-editor-image7.png)



