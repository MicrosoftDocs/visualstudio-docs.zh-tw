---
title: 什麼是偵錯？
description: 瞭解用來對應用程式進行偵錯工具的意義
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3435b7a270d89dc38f5ff10a1350418a24f91c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883931"
---
# <a name="what-is-debugging"></a>什麼是偵錯？

Visual Studio 偵錯工具是一項功能強大的工具。 在示範如何使用它之前，我們想要先討論一些詞彙，例如調試 *程式*、 *調試* 程式和 *偵錯工具模式*。 如此一來，當我們稍後討論尋找和修正 bug 時，我們就會討論相同的事情。

## <a name="debugger-vs-debugging"></a>偵錯工具與偵錯工具

錯錯 *詞彙可以* 表示許多不同的專案，但實際上，這表示從您的程式碼中移除 bug。 現在有很多方法可以這麼做。 例如，您可能會藉由掃描您的程式碼來尋找錯誤，或使用程式碼分析器來進行 debug。 您可以使用效能分析工具來進行程式碼的偵錯工具。 或者，您可以使用調試 *程式* 來進行 debug。

偵錯工具是一種非常特製化的開發人員工具，可附加到執行中的應用程式，並可讓您檢查程式碼。 在 Visual Studio 的偵錯工具檔中，這通常是我們說「偵錯工具」時所指的意思。

## <a name="debug-mode-vs-running-your-app"></a>Debug 模式與執行您的應用程式

當您第一次在 Visual Studio 中執行您的應用程式時，您可以在工具列中按下綠色箭號按鈕 ![開始調試](../debugger/media/dbg-tour-start-debugging.png "[偵錯]") 程式 (或 **F5**) 來啟動應用程式。 根據預設， **Debug** 值會出現在左邊的下拉式清單中。 如果您不熟悉 Visual Studio，這可能會讓您的應用程式在執行應用程式時，有一些需要執行的工作，也就是執行您的應用程式--但是這些基本上是兩個非常不同的工作。

![選取 Debug build](../debugger/media/what-is-debugging-debug-build.png)

**Debug** 值表示 debug 設定。 當您啟動應用程式 (在偵錯工具中按下綠色箭號或 **F5**) 時，您會在「偵錯工具」 *模式* 中啟動應用程式，這表示您正在執行應用程式並附加偵錯工具。 這會啟用一組完整的偵錯工具，可讓您用來協助找出應用程式中的 bug。

如果您已開啟專案，請選擇下拉式清單選取器，其中會顯示 **Debug** ，並改為選擇 [ **發行** ]。

![選取發行組建](../debugger/media/what-is-debugging-release-build.png)

當您切換此設定時，您會將專案從偵錯工具設定變更為發行設定。 Visual Studio 專案針對您的程式具有不同的版本和偵錯組態。 您會建立偵錯工具的偵錯工具版本，以及最終發行版本散發的發行版本。 發行組建已針對效能優化，但 debug 組建較適合用於偵錯工具。

## <a name="when-to-use-a-debugger"></a>使用偵錯工具的時機

偵錯工具是在您的應用程式中尋找和修正 bug 的基本工具。 不過，內容是最重要的，而且請務必利用您可處置的所有工具，以協助您快速排除錯誤或錯誤。 有時候，適當的「工具」可能是更好的編碼作法。 藉由學習何時使用偵錯工具和其他工具，您也將瞭解如何更有效地使用偵錯工具。

## <a name="next-steps"></a>下一步

在本文中，您已了解幾個一般偵錯概念。 接下來，您可以開始瞭解如何使用 Visual Studio 進行偵錯工具，以及如何撰寫程式碼較少的 bug。 下列文章說明 c # 程式碼範例，但這些概念適用于 Visual Studio 支援的所有語言。

> [!div class="nextstepaction"]
> [適合完全初學者的偵錯](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
