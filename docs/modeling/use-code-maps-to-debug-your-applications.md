---
title: 使用 Code Map 偵錯您的應用程式
description: 瞭解如何使用 code map，以協助您避免遺失大型程式碼基底、不熟悉的程式碼或舊版程式碼。
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d935ee5c4341a2d625c6f85226cc649d696d6e6e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729388"
---
# <a name="use-code-maps-to-debug-your-applications"></a>使用 Code Map 偵錯您的應用程式

Code Map 有助於避免在大型程式碼基底、不熟悉的程式碼或舊版程式碼當中不知所措。 例如，當您要進行偵錯工具時，您可能必須跨多個檔案和專案查看程式碼。 使用 Code Map 巡覽程式碼片段並了解它們之間的關聯性。 如此一來，您就不必在腦中持續追蹤此程式碼，或繪製個別的圖表。 因此，當您工作中斷時，Code Map 可協助重新整理您正在處理之程式碼的記憶。

![Code map &#45; 對應程式碼中的關聯性](../modeling/media/codemapstoryboardpaint.png)

**綠色箭號會顯示游標出現在編輯器中的位置**

如需使用 code map 時可使用的命令和動作的詳細資訊，請參閱 [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

> [!NOTE]
> 若要建立和編輯 code map，您需要 Visual Studio Enterprise 版。 在 Visual Studio Community 和專業版中，您可以開啟在 Enterprise edition 中產生的圖表，但無法編輯它們。

## <a name="understand-the-problem"></a>了解問題
 假設您處理的繪圖程式有 Bug。 若要重現 bug，請在 Visual Studio 中開啟方案，然後按 **F5** 開始進行調試。

 當您繪製線條並選擇 [ **復原我的最後一個筆觸**] 時，在您繪製下一行時，不會發生任何動作。

 ![Code map &#45; 重現 bug](../modeling/media/codemapstoryboardpaint0.png)

 因此您藉由搜尋 `Undo` 方法開始調查。 您會在`PaintCanvas` 類別中找到。

 ![Code map &#45; 尋找程式碼](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>開始製作程式碼地圖
 現在開始對應 `undo` 方法及其關聯性。 在程式碼編輯器中，您將 `undo` 方法及其參考的欄位加入至新的 Code Map。 當您建立新的對應時，可能需要一些時間為程式碼編製索引。 這有助於後面的作業更快速執行。

 ![Code map &#45; 顯示方法和相關欄位](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> 加入對應的最後一個項目會以綠色反白顯示。 綠色箭號會顯示游標在程式碼中的位置。 項目之間的箭頭表示不同的關聯性。 您可以藉由在周圍移動滑鼠和檢查工具提示，來取得對應上之項目的詳細資訊。

 ![Code map &#45; 顯示工具提示](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>從地圖中巡覽和檢查程式碼
 若要查看每個欄位的程式碼定義，請按兩下地圖上的欄位或選取欄位，然後按下 **F12**。 綠色箭頭會在對應中的項目之間移動。 您在程式碼編輯器中的游標也會自動移動。

 ![已選取歷程記錄欄位之 code map 視窗的螢幕擷取畫面，以及反白顯示所有歷程記錄實例的程式碼編輯器視窗。](../modeling/media/codemapstoryboardpaint5.png)

 ![已選取 [paintObjects] 欄位的 code map 視窗的螢幕擷取畫面，以及反白顯示 paintObjects 所有實例的程式碼編輯器視窗。](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> 您也可以在程式碼編輯器中移動游標來移動對應上的綠色箭頭。

## <a name="understand-relationships-between-pieces-of-code"></a>了解程式碼之間的關聯性
 現在您想知道哪些其他程式碼與 `history` 及 `paintObjects` 欄位互動。 您可以將所有參考這些欄位的方法加入至對應。 您可以從對應或程式碼編輯器執行此步驟。

 ![Code map &#45; 尋找所有參考](../modeling/media/codemapstoryboardpaint6.png)

 ![從程式碼編輯器中開啟 Code Map](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> 如果您從跨多個應用程式 (如 Windows Phone 或 Windows 市集) 共用的專案中加入項目，則這些項目將一律與目前作用中的應用程式專案一起出現在對應上。 因此，如果您將內容變更為另一個應用程式專案，對應上的內容也會為任何來自共用專案的新增項目進行變更。 您使用對應中項目執行的作業僅適用於共用相同內容的項目。

 變更配置以重新排列關聯性流程，使對應更容易閱讀。 您也可以透過拖曳的方式將項目在對應間移動。

 ![[Code map] 視窗的螢幕擷取畫面，其中已開啟 [版面配置] 功能表，並已選取 [左方至 Rgiht] 命令。](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> 依預設，會開啟 [累加 **式版面** 配置]。 當您加入新項目時，這會盡可能減少重新排列對應。 若要在每次加入新專案時重新排列整個對應，請關閉 [累加 **式版面** 配置]。

 ![Code map 視窗的螢幕擷取畫面，其中欄位之間的 relationshiop 箭號是由左至右。](../modeling/media/codemapstoryboardpaint7.png)

 我們來檢查這些方法。 在對應上，按兩下 [ **PaintCanvas** ] 方法，或選取此方法並按下 **F12**。 您了解這個方法會將 `history` 和 `paintObjects` 建立為空白清單。

 ![已選取 PaintCanvas 方法之 code map 視窗的螢幕擷取畫面，以及顯示反白顯示 PainCanvas 方法名稱的程式碼片段影像。](../modeling/media/codemapstoryboardpaint8.png)

 現在重複相同步驟來檢查 `clear` 方法定義。 您了解 `clear` 會對 `paintObjects` 和 `history` 執行某些工作。 然後呼叫 `Repaint` 方法。

 ![已選取 Clear 方法的 code map 視窗的螢幕擷取畫面，以及顯示 Clear 方法程式碼的程式碼片段影像。](../modeling/media/codemapstoryboardpaint9.png)

 現在檢查 `addPaintObject` 方法定義。 它也會對 `history` 和 `paintObjects` 執行某些工作。 它也會呼叫 `Repaint`。

 ![已選取 addPaintObject 方法之 code map 視窗的螢幕擷取畫面，以及顯示 addPaintObject 方法程式碼的程式碼片段影像。](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>檢查地圖找出問題
 似乎所有修改 `history` 和 `paintObjects` 的方法都會呼叫 `Repaint`。 但 `undo` 方法不會呼叫 `Repaint`，即使 `undo` 會修改相同的欄位。 因此您認為可以從 `Repaint` 呼叫 `undo` 解決這個問題。

 ![Code map &#45; 尋找遺漏的方法呼叫](../modeling/media/codemapstoryboardpaint11.png)

 如果您沒有對應顯示這個遺漏的呼叫，可能難以發現這個問題，特別是在較複雜的程式碼中。

## <a name="share-your-discovery-and-next-steps"></a>共用您的探索和後續步驟
 在您或其他人修正此 Bug 之前，您可以在對應上記下關於問題和修正方式的附註。

 ![Code map &#45; 批註和旗標專案以進行後續追蹤](../modeling/media/codemapstoryboardpaint12.png)

 例如，您可以使用色彩加入註解至對應和旗標項目。

 ![Code map &#45; 已加上批註和旗標的專案](../modeling/media/codemapstoryboardpaint12a.png)

 如果您有安裝 Microsoft Outlook，您可以用電子郵件將對應傳送給其他人。 您也可以將對應匯出為影像或其他格式。

 ![Code map &#45; 共用、匯出、郵件](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>解決問題並顯示您的作法
 若要修正這個 Bug，您必須將對 `Repaint` 的呼叫加入至 `undo`。

 ![Code map &#45; 新增遺漏的方法呼叫](../modeling/media/codemapstoryboardpaint14.png)

 若要確認您的修正，先重新啟動偵錯工作階段，然後嘗試重現 Bug。 現在選擇 [ **復原我的最後一個筆觸** ] 會如您預期般運作，並確認您已進行正確的修正。

 ![Code map &#45; 確認程式碼修正](../modeling/media/codemapstoryboardpaint15.png)

 您可以更新對應以顯示您所做的修正。

 ![Code map &#45; 使用遺漏的方法呼叫更新對應](../modeling/media/codemapstoryboardpaint16.png)

 您的地圖現在會顯示 **復原** 和重新 **繪製** 之間的連結。

 ![Code map &#45; 使用方法呼叫來更新對應](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> 當您更新對應時，可能會看到訊息，指出用於建立對應的程式碼索引已更新。 這表示有人變更程式碼，使您的對應與目前的程式碼不符。 這不會阻止您更新對應，不過，您可能必須重新建立對應以確認其符合程式碼。

 現在您已經完成調查。 您藉由對應程式碼成功找到問題並且加以解決。 您還可以利用對應巡覽程式碼、記住您所學到的內容，以及顯示您用於解決問題的步驟。

## <a name="see-also"></a>請參閱

- [進行偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [視覺化程式碼](../modeling/visualize-code.md)
