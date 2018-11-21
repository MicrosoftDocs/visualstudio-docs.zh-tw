---
title: 使用 code map 偵錯應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 51
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: af5f34b307f94f1bae4c913421acbe0a934ed113
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743826"
---
# <a name="use-code-maps-to-debug-your-applications"></a>使用 Code Map 偵錯您的應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Code Map 有助於避免在大型程式碼基底、不熟悉的程式碼或舊版程式碼當中不知所措。 例如，當您在偵錯時，可能必須查看許多檔案和專案的程式碼。 使用 Code Map 巡覽程式碼片段並了解它們之間的關聯性。 如此一來，您就不必在腦中持續追蹤此程式碼，或繪製個別的圖表。 因此，當您工作中斷時，Code Map 可協助重新整理您正在處理之程式碼的記憶。  
  
 ![程式碼對應&#45;對應程式碼中的關聯性](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **綠色箭頭顯示游標出現在編輯器中的位置**  
  
 如需命令和使用 code map 時，您可以使用的動作的詳細資訊，請參閱 <<c0> [ 瀏覽和重新整理 code map](../modeling/browse-and-rearrange-code-maps.md)。  
  
## <a name="understand-the-problem"></a>了解問題  
 假設您處理的繪圖程式有 Bug。 若要重現 bug，您必須開啟解決方案 Visual Studio，然後按下**F5**開始偵錯。  
  
 當您繪製一條線，並選擇**復原前一次筆觸**，直到您繪製下一行，會發生任何事。  
  
 ![程式碼對應&#45;重新產生 bug](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 因此您藉由搜尋 `Undo` 方法開始調查。 您會在`PaintCanvas` 類別中找到。  
  
 ![程式碼對應&#45;尋找程式碼](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## <a name="start-mapping-the-code"></a>開始製作程式碼地圖  
 現在開始對應 `undo` 方法及其關聯性。 在程式碼編輯器中，您將 `undo` 方法及其參考的欄位加入至新的 Code Map。 當您建立新的對應時，可能需要一些時間為程式碼編製索引。 這有助於後面的作業更快速執行。  
  
 ![程式碼對應&#45;方法和相關的欄位顯示](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  加入對應的最後一個項目會以綠色反白顯示。 綠色箭頭顯示指標在程式碼中的位置。 項目之間的箭頭表示不同的關聯性。 您可以藉由在周圍移動滑鼠和檢查工具提示，來取得對應上之項目的詳細資訊。  
  
 ![程式碼對應&#45;顯示工具提示](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## <a name="navigate-and-examine-code-from-the-map"></a>從地圖中巡覽和檢查程式碼  
 若要查看每個欄位的程式碼定義，按兩下對應上的欄位，或選取欄位，然後按**F12**。 綠色箭頭會在對應中的項目之間移動。 您在程式碼編輯器中的游標也會自動移動。  
  
 ![程式碼對應&#45;檢查欄位定義](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![程式碼對應&#45;檢查欄位定義](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  您也可以在程式碼編輯器中移動游標來移動對應上的綠色箭頭。  
  
## <a name="understand-relationships-between-pieces-of-code"></a>了解程式碼之間的關聯性  
 現在您想知道哪些其他程式碼與 `history` 及 `paintObjects` 欄位互動。 您可以將所有參考這些欄位的方法加入至對應。 您可以從對應或程式碼編輯器執行此步驟。  
  
 ![程式碼對應&#45;尋找所有參考](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![從程式碼編輯器中開啟 code map](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  如果您從跨多個應用程式 (如 Windows Phone 或 Windows 市集) 共用的專案中加入項目，則這些項目將一律與目前作用中的應用程式專案一起出現在對應上。 因此，如果您將內容變更為另一個應用程式專案，對應上的內容也會為任何來自共用專案的新增項目進行變更。 您使用對應中項目執行的作業僅適用於共用相同內容的項目。  
  
 變更配置以重新排列關聯性流程，使對應更容易閱讀。 您也可以透過拖曳的方式將項目在對應間移動。  
  
 ![程式碼對應&#45;變更版面配置](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  根據預設，**累加配置**已開啟。 當您加入新項目時，這會盡可能減少重新排列對應。 若要重新排列整個對應，每次您新增新的項目，請關閉**累加配置**。  
  
 ![程式碼對應&#45;變更版面配置](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 我們來檢查這些方法。 在地圖上，按兩下**PaintCanvas**方法，或選取此方法並按**F12**。 您了解這個方法會將 `history` 和 `paintObjects` 建立為空白清單。  
  
 ![程式碼對應&#45;檢查方法定義](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 現在重複相同步驟來檢查 `clear` 方法定義。 您了解 `clear` 會對 `paintObjects` 和 `history` 執行某些工作。 然後呼叫 `Repaint` 方法。  
  
 ![程式碼對應&#45;檢查方法定義](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 現在檢查 `addPaintObject` 方法定義。 它也會對 `history` 和 `paintObjects` 執行某些工作。 它也會呼叫 `Repaint`。  
  
 ![程式碼對應&#45;檢查方法定義](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## <a name="find-the-problem-by-examining-the-map"></a>檢查地圖找出問題  
 似乎所有修改 `history` 和 `paintObjects` 的方法都會呼叫 `Repaint`。 但 `undo` 方法不會呼叫 `Repaint`，即使 `undo` 會修改相同的欄位。 因此您認為可以從 `Repaint` 呼叫 `undo` 解決這個問題。  
  
 ![程式碼對應&#45;尋找遺漏的方法呼叫](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 如果您沒有對應顯示這個遺漏的呼叫，可能難以發現這個問題，特別是在較複雜的程式碼中。  
  
## <a name="share-your-discovery-and-next-steps"></a>共用您的探索和後續步驟  
 在您或其他人修正此 Bug 之前，您可以在對應上記下關於問題和修正方式的附註。  
  
 ![程式碼對應&#45;註解和旗標以便後續追蹤的項目](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 例如，您可以使用色彩加入註解至對應和旗標項目。  
  
 ![程式碼對應&#45;已註解和標有旗標的項目](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 如果您有安裝 Microsoft Outlook，您可以用電子郵件將對應傳送給其他人。 您也可以將對應匯出為影像或其他格式。  
  
 ![程式碼對應&#45;共用，匯出，mail](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## <a name="fix-the-problem-and-show-what-you-did"></a>解決問題並顯示您的作法  
 若要修正這個 Bug，您必須將對 `Repaint` 的呼叫加入至 `undo`。  
  
 ![程式碼對應&#45;將遺漏的方法呼叫加入](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 若要確認您的修正，先重新啟動偵錯工作階段，然後嘗試重現 Bug。 現在選擇**復原前一次筆觸**如預期般運作，並確認您已進行正確的修正。  
  
 ![程式碼對應&#45;確認程式碼修正](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 您可以更新對應以顯示您所做的修正。  
  
 ![程式碼對應&#45;與遺漏的方法呼叫的更新對應](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 您的地圖現在會顯示之間的連結**恢復**並**重新繪製**。  
  
 ![程式碼對應&#45;方法呼叫的已更新地圖](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  當您更新對應時，可能會看到訊息，指出用於建立對應的程式碼索引已更新。 這表示有人變更程式碼，使您的對應與目前的程式碼不符。 這不會阻止您更新對應，不過，您可能必須重新建立對應以確認其符合程式碼。  
  
 現在您已完成調查。 您藉由對應程式碼成功找到問題並且加以解決。 您還可以利用對應巡覽程式碼、記住您所學到的內容，以及顯示您用於解決問題的步驟。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [視覺化程式碼](../modeling/visualize-code.md)



