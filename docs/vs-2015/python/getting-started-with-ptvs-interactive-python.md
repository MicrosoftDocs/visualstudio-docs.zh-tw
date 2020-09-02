---
title: 開始使用 PTVS：互動式 Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550983"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>PTVS 快速入門：互動式 Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

互動式提示或讀取 - 求值 - 輸出迴圈 (REPL) 是高產能程式設計語言的重要工具。  它們可讓您執行程式碼片段來探索和學習 API，使用 API 進行實驗，並以互動方式開發可運作的程式碼，以包含在專案或程式中。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) 中觀看這些指示。  
  
 在 [Python 環境] 視窗中，您會看到一份您所有 Python 環境的清單。  您可以選取其中任何一項來開啟互動式視窗或 REPL。  如果您曾經在命令提示字元中執行過 Python.exe，則您之前就已見過 Python REPL。  REPL 會提示您，而且您可以輸入程式碼，按 Enter 鍵然後立即查看程式碼結果。  這是包含所有執行、變數指派等所有狀態的即時執行內容。 您可以參考在稍後提交至複寫提示時保留結果的變數。  您可以撰寫多行程式碼，並一次就執行全部 (例如方法宣告或多個陳述式)。  
  
 當您開始使用新的程式庫時，REPL 是嘗試程式庫的好方法。  您可以匯入程式庫，檢查子封裝、類別和函式。  Python 可透過其 `help()` 函式告訴您所有資訊。  此外，Python Tools for Visual Studio (PTVS) 可給您以編輯器中使用的程式碼模型為基礎的建議和文件，而不需要執行程式庫。  當您執行程式碼時，PTVS 會使用來自 Python 執行階段的資訊以改善 PTVS 建議。  
  
 [互動式視窗] 也可用於反覆或演化的程式碼開發，包含當您在開發時測試程式碼。  您可以在編輯器視窗中選取函式，請按右指標按鈕，並選擇 [傳送至互動式]。  此命令會將選取範圍複製到 [互動式視窗] 做為下一個輸入並執行。  您可立即查看結果。  如果您需變更先前的輸入，您可以按向上鍵，以取回程式碼，請修改它，並按下 Ctrl + Enter 來執行程式碼。  在輸入結束後按下 Enter 鍵執行，但在輸入中間按下 Enter 鍵則會插入一個新行。  
  
 您可以視需要為每個 Python 安裝開啟一個 [互動式視窗]。  視窗頂端有一些按鈕可清除顯示、重設執行內容等等。 您的歷程記錄將保持不變。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) 中觀看這些指示。  
  
## <a name="see-also"></a>另請參閱  
 [Wiki 檔](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [PTVS 快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
