---
title: 步驟 9：嘗試其他功能
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2d32a0d2e208b5f8bfd7869c8dfa92f063f1db5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925939"
---
# <a name="step-9-try-other-features"></a>步驟 9：嘗試其他功能
若要了解詳細資訊，請試著變更圖示和色彩、加入遊戲計時器，以及加入音效。 若要讓遊戲更具挑戰性，請試著使戲局變大並調整計時器。

 若要下載這個範例的完整版，請參閱[完整的配對遊戲教學課程範例](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) \(英文\)。

## <a name="to-try-other-features"></a>若要嘗試其他功能

-   以您選擇的圖示和色彩予以取代。

    > [!TIP]
    >  嘗試查看標籤的 [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) 屬性。

-   加入遊戲計時器，追蹤玩家過關所需的時間。

    > [!TIP]
    >  若要這樣做，您可以加入標籤以便在 <xref:System.Windows.Forms.TableLayoutPanel> 上方的表單上顯示已耗用的時間，並將另一個計時器加入至表單以追蹤時間。 請使用程式碼在玩家啟動遊戲時啟動計時器，並在配對最後兩個圖示之後停止計時器。

-   加入當玩家找到配對項目時的音效、當玩家發現不相符的兩個圖示時的另一種音效，以及當程式再次隱藏圖示時的第三種音效。

    > [!TIP]
    >  若要播放音效，您可以使用 <xref:System.Media> 命名空間。 如需詳細資訊，請參閱 [在 Windows Forms 應用程式中播放音效 (C#)](http://youtu.be/qOh4ooHg1UU) \(英文\) 或 [如何在 Visual Basic 中播放音訊](http://youtu.be/-4oPDeQrtMs) \(英文\)。

-   使戲局變大，可讓遊戲變得更困難。

    > [!TIP]
    >  您需要做的不僅是將資料列及資料行新增至 TableLayoutPanel，還需要考量您所建立的圖示數目。

-   如果玩家的速度太慢回應而且並未在特定時間內及時選擇第二個圖示，則隱藏第一個圖示，可讓遊戲更具挑戰性。

## <a name="to-continue-or-review"></a>若要繼續或檢視

-   如果您碰到程式開發的問題，請嘗試發表問題至 MSDN 論壇。 請參閱 [Visual Basic 論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral)和 [Visual C# 論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral)。

-   其中提供了很好的免費視訊學習資源。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic fundamentals:Development for absolute beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Visual Basic 基本概念：適合完全初學者的開發)。 若要深入了解 Visual C# 中的程式設計，請參閱 [C# fundamentals:Development for absolute beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (C# 基本概念：適合完全初學者的開發)。

-   若要回到上一個教學課程步驟，請參閱[步驟 8：新增驗證玩家是否勝利的方法](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)。
