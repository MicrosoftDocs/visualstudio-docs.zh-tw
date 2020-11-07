---
title: Visual Studio Tools for Unity | Microsoft Docs
description: 閱讀有關 Visual Studio Tools for Unity 的總覽，這是免費的 Visual Studio 延伸模組，可協助您使用 Unity 開發跨平臺遊戲和應用程式。
ms.custom: ''
ms.date: 10/25/2019
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: overview
ms.assetid: 6cabc626-5310-4622-a743-210a9abb5535
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: ee4e9e0dc9df4eb5decb3fc9c2afb0411e9cb75c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341532"
---
# <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity
![Visual Studio Tools for Unity](../media/hero.png)

## <a name="overview"></a>概觀
Visual Studio Tools for Unity 是一種免費的 Visual Studio 延伸模組，可將 Visual Studio 轉換為使用 Unity 開發跨平台遊戲和應用程式的功能強大工具。

Unity 編輯器適合用來組合您的遊戲世界，但無法在該編輯器中撰寫程式碼。 您可運用 Visual Studio Tools for Unity，使用熟悉的 Visual Studio 程式碼編輯、偵錯與提升生產力的功能，用 C# 為 Unity 專案建立編輯器與遊戲指令碼，也可以使用 Visual Studio 的強大偵錯功能，對這些指令碼進行偵錯。

不僅如此，Visual Studio Tools for Unity 還與 Unity Editor 緊密整合，因此您可以花較少時間來回切換執行簡單工作，它也提供 Unity 特有的提升產能功能，並將 Unity 文件放在您可以隨時取得的位置。

### <a name="compatible-with-visual-studio-community-on-windows-and-macos-and-bundled-with-unity"></a>與 Windows 和 macOS 上的 Visual Studio Community 相容，並與 Unity 配套
Visual Studio 和 Visual Studio for Mac 的社區都可免費使用，並與 Unity 安裝配套。 如需安裝和設定的詳細資訊，請造訪 Visual Studio Tools for Unity 使用者 [入門檔](getting-started-with-visual-studio-tools-for-unity.md) 。

## <a name="intellisense-for-unity-messages"></a>Unity 訊息的 IntelliSense
IntelliSense 程式碼編譯可快速且輕鬆地[實作 Unity API 訊息](using-visual-studio-tools-for-unity.md#intellisense-for-unity-api-messages) (例如 `OnCollisionEnter`)，包含其參數。

![顯示 OnCollisionEnter 的 IntelliSense 對話方塊](../media/vs/intellisense-example.png)

## <a name="superior-debugging"></a>高階偵錯
Visual Studio Tools for Unity 支援預期從 Visual Studio 取得的強大[偵錯](using-visual-studio-tools-for-unity.md#unity-debugging)功能：

* 設定中斷點，包含條件式中斷點。
* 在監看式視窗中評估複雜的運算式。
* 檢查及修改變數和引數的值。
* 向下切入至複雜的物件和資料結構。

![在檢查變數的中斷點上停止](../media/vs/debugging-inspecting.png)

## <a name="integrated-suggestions-for-best-practices-and-performance-insights"></a>最佳做法與效能深入解析的整合建議
撰寫更好的程式碼，利用 Visual Studio 對 Unity 專案的深入瞭解，來取得最佳做法。

![VS 重構字串與 CompareTag 的比較](../media/vs/unity-diagnostics.png)

## <a name="codelens-support-for-unity-scripts-and-messages"></a>Unity 腳本和訊息的 CodeLens 支援
Unity 腳本和訊息函式是以提示裝飾，可讓您更輕鬆地辨識 Unity 所提供的內容，以及您的程式碼。

 ![新的腳本，顯示 Unity 腳本和 Unity 訊息的 CodeLens 提示](../media/vs/codelens-support.png)

> [!NOTE]
> CodeLens 支援可在 Visual Studio 2019 中取得。

## <a name="optimized-view-of-all-your-scripts-to-match-unity"></a>優化所有腳本的視圖以符合 Unity
Unity Project Explorer (UPE) 是透過標準方案總管來查看專案檔的替代方法。 UPE 會篩選所顯示的檔案，並將它們顯示在符合 Unity ( **View > Unity Project Explorer** 的階層中 Visual Studio 2019) 。

![Unity Project Explorer](../media/vs/unity-project-explorer.png)

> [!NOTE]
> Unity Project Explorer 可在 Visual Studio 2019 中取得。 在 Visual Studio for Mac 中，Solution Pad 預設會有 Unity 專案的類似行為-不需要額外的視圖。

* [Visual Studio Tools for Unity 使用者入門](getting-started-with-visual-studio-tools-for-unity.md)
