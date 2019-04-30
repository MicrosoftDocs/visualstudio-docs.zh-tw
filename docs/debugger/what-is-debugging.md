---
title: 什麼是偵錯？
description: 了解偵錯應用程式的意義
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01317f3b8fa92cf1bc17c3745f708e0d3f26e5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901214"
---
# <a name="what-is-debugging"></a>什麼是偵錯？

Visual Studio 偵錯工具是一個功能強大的工具。 我們示範如何使用它之前，我們想要這類討論的一些術語*偵錯工具*，*偵錯*，並*偵錯模式*。 如此一來，當我們談到稍後找出並修正 bug，我們將討論相同的動作。

## <a name="debugger-vs-debugging"></a>偵錯工具與偵錯

詞彙*偵錯*可以表示不同的東西，很多，但是最常值，表示移除您的程式碼中的 bug。 現在，有很多方法可以執行這項操作。 例如，您可能會偵錯掃描程式碼，尋找有錯字，或使用程式碼分析工具。 若要偵錯程式碼，可能會使用效能分析工具。 或者，您可能會使用偵錯*偵錯工具*。

偵錯工具是一種非常特殊的開發人員工具，附加至您執行的應用程式，並可讓您檢查您的程式碼。 在 Visual Studio 的偵錯文件，這通常是什麼意思是說 「 偵錯 」。

## <a name="debug-mode-vs-running-your-app"></a>偵錯模式與執行您的應用程式

當您第一次，在 Visual Studio 中執行您的應用程式時，可能會開始藉由按下綠色箭號按鈕![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")工具列中 (或**F5**)。 根據預設，**偵錯**值會出現在左側下拉式清單。 如果您是剛接觸 Visual Studio，這可能讓偵錯您的應用程式已執行和的印象您的應用程式-它，但這些基本上是兩個非常不同的工作。

![選取 偵錯組建](../debugger/media/what-is-debugging-debug-build.png)

A**偵錯**值表示偵錯組態。 當您啟動應用程式 (按綠色箭號，或**F5**) 在偵錯組態中，您必須啟動應用程式*偵錯模式*，這表示您正在附加偵錯工具執行您的應用程式。 這可讓一組完整的偵錯功能，可用來協助找出您的應用程式中的 bug。

如果您開啟一個專案，請選擇的下拉式清單選取器，該處會指示**偵錯**，然後選擇**發行**改。

![選取的發行組建](../debugger/media/what-is-debugging-release-build.png)

當您切換此設定時，您將專案變更從偵錯組態來發行組態。 Visual Studio 專案針對您的程式具有不同的版本和偵錯組態。 建立偵錯的偵錯版本和最後發行散發的發行版本。 發行組建已最佳化的效能，但偵錯組建更適合用來偵錯。

## <a name="when-to-use-a-debugger"></a>使用偵錯工具的時機

偵錯工具是不可或缺的工具，尋找並修正您的應用程式中的 bug。 不過，內容成為王道，而且務必要運用在您的可處置，可協助您快速地消除 bug 或錯誤的所有工具。 某些情況下，「 工具 」 的權限可能是更好的程式碼撰寫做法。 藉由學習何時使用其他工具與偵錯工具，您也將學習如何更有效地使用偵錯工具。

## <a name="next-steps"></a>後續步驟

在本文中，您已了解幾個一般偵錯概念。 接下來，您可以開始學習如何使用 Visual Studio 偵錯，以及撰寫程式碼較少的 bug。 下列文章顯示C#程式碼範例，但概念適用於 Visual Studio 所支援的所有語言。

> [!div class="nextstepaction"]
> [適合完全初學者的偵錯](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
