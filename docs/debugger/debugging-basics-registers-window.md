---
title: 關於暫存器視窗 |Microsoft Docs
description: 瞭解 Visual Studio 中的 [暫存器] 視窗，只有在 [選項] 對話方塊的 [偵錯工具] 節點中啟用位址層級的偵錯工具時才能使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62425913e65207953554a35054399fb8a6d2af4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728469"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>關於 Visual Studio (c #、c + +、Visual Basic、F # 中的 [暫存器] 視窗 ) 

只有在透過 [選項] 對話方塊的 [偵錯] 節點啟用位址層級偵錯時，才可以使用 [暫存器] 視窗。

 暫存器是處理器 (CPU) 中的特殊位置，用來儲存處理器正在使用中的小型資料。 編譯或解譯原始程式碼將會根據需要，產生可將資料從記憶體移到暫存器，以及從暫存器移回記憶體的指示。 和存取記憶體內的資料相比，存取暫存器資料的速度非常快，因此允許處理器將資料留在暫存器內並重複存取的程式碼在執行方面，會比需要處理器經常載入與卸載暫存器的程式碼快很多。 為了讓編譯器可以更容易將資料保存於暫存器內，並執行其他的最佳化處理，您應該避免使用全域變數，盡可能使用區域變數。 用這種方式撰寫的程式碼，通常都會具有良好的參考位置。 使用某些語言時 (例如，C/C++)，程式設計人員可宣告一個暫存器變數 (Register Variable)，要求編譯器盡量將該變數保留在暫存器內。 如需詳細資訊，請參閱 [Register 關鍵字](/previous-versions/482s4fy9(v=vs.140))。

 暫存器可分成兩種類型：一般用途和特殊用途。 一般用途的暫存器可包含一般作業的資料，例如將兩個數值相加，或參考陣列中的某個項目。 特殊用途的暫存器具有特定用途和特殊意義。 堆疊指標暫存器就是一個好例子，處理器可用它來追蹤程式的呼叫堆疊。 做為一個程式設計人員，您可能不會直接去使用堆疊指標。 不過，這對於程式的正常運作來說是很重要的，因為若沒有堆疊指標，處理器就不知道在函式呼叫的端點時，該返回何處。

 大部分一般用途的暫存器只會儲存單一資料項目。 例如，單精確度整數、浮點數或陣列的元素。 有些較新的處理器具有較大的暫存器，稱為向量暫存器，它可包含小型的資料陣列。 因為它們可包含許多資料，向量暫存器可讓牽涉到陣列的作業更快地執行。 向量暫存器一開始用於昂貴的高效能超級電腦上，不過現在已可用於微處理器上，以便更有效地處理大量的圖形作業。

 處理器通常擁有兩組一般用途的暫存器，一組適用於浮點作業，另一組則適用於整數作業。 顯而易見地，這些就是浮點和整數暫存器。

 Managed 程式碼會在執行階段編譯為機器碼，以便存取微處理器的實體暫存器。 [暫存器] 視窗會為 Common Language Runtime 或機器碼顯示這些實體暫存器。 [暫存器] 視窗並不會顯示指令碼或 SQL 應用程式的暫存器資訊，因為指令碼和 SQL 都是不支援暫存器概念的語言。

 如需顯示 [暫存器] 視窗的詳細資訊，請參閱[使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)。

 當您 **查看 [緩存** 器] 視窗時，您會看到像這樣的專案 `EAX = 003110D8` 。

 符號左邊的符號是暫存器 `=` 名稱， `EAX` 在此案例中為。 `=` 號右邊的數值代表暫存器的內容。

 [暫存器] 視窗不僅可以讓您檢視暫存器的內容。 當您處於機器碼的中斷模式時，可按一下暫存器的內容，並編輯其數值。 但是您不應該任意進行這個動作。 除非您很了解正在編輯的暫存器和它所包含的資料，否則隨意編輯可能會導致程式損毀或其他不希望得到的結果。 可惜的是，各種 Intel 和 Intel 相容處理器的暫存器組合之詳細資訊不屬於本簡介說明範圍之列。

## <a name="register-groups"></a>註冊群組

為了減少雜亂，[暫存器] 視窗會將暫存器組織成群組。 如果您以滑鼠右鍵按一下 [暫存器] 視窗，將會看到包含群組清單的捷徑功能表，就可依適合的方式加以顯示或隱藏。

## <a name="register-flags"></a>註冊旗標

針對 Intel x86 處理器，您可能 **會在 [暫存器] 視窗** 中看到下列旗標。 在偵測會話期間，您也可以編輯這些旗標。

|旗標|設定值|
|-|-|
|溢位|OV = 1|
|方向|向上 = 1|
|中斷|EI = 1|
|簽署|PL = 1|
|零個|ZR = 1|
|輔助執行|AC = 1|
|Parity|PE = 1|
|Carry|CY = 1|

## <a name="see-also"></a>請參閱
- [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)