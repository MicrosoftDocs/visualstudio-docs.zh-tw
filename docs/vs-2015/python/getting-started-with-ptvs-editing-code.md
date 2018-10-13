---
title: Ptvs 快速入門： 編輯程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: ef0a84523a2d828e696fb50f641f392ab7bbd39f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265781"
---
# <a name="getting-started-with-ptvs-editing-code"></a>PTVS 快速入門：編輯程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS 為 Python 提供高產能的 Visual Studio 編輯器體驗。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) 中觀看這些指示。  
  
 從空的 Python 基本應用程式專案範本開始。  
  
 在編輯器中開始輸入一行 `from … import`。  您會看到快顯的完成清單，完整列出可供匯入的模組。  這份清單會因您的 Python 版本及所安裝的程式庫而異。  請使用數學程式庫做為範例。  您會注意到當您輸入時，完成清單會篩選這些項目，包含您所輸入的字元。  匯入 `sin` 識別項以完成陳述式。  
  
```python  
from math import sin  
  
```  
  
 在撰寫程式碼時，如果您使用未繫結但可在程式庫中找到的識別項，則 PTVS 會提供快顯的快速檢修，用來加入您所需的適當匯入陳述式。  例如，如果您鍵入`cos`，那麼您會看到**數學從匯入**提供。  
  
 您可以使用程式碼片段來產生程式碼。  在 [編輯] 功能表中，選擇 [IntelliSense]，然後選擇 [插入程式碼片段]。  現在請選擇 [Python]，然後選擇 [def]。呼叫函式 `make_dot_string` 並加入一個參數 `x`。  您現在可以在檔案中加入判斷提示，來進行測試導向開發，而且您會看到 PTVS 已經可以在完成清單內提供新的函式。  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 現在回到新的函式，並且開始撰寫下列主體：  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 您會看到 PTVS 假設此參數是一個整數，因為 PTVS 分析過此函式的呼叫位置。   您也必須使用快速修正來匯入 `radians`。  
  
 在最上層輸入 `main`，叫用智慧標籤 UI，並使用索引標籤選擇 "def main ..."，以使用另一個程式碼片段建立主要區塊  撰寫基本迴圈來呼叫 `make_dot_string`。  如果您按下句號並查看所提供的完成，您會看到 PTVS 知道此函式會傳回字串。  此類型資訊會在整個程式中傳播，因此不論您的值最後到達哪裡，我們都可提供工具提示和完成，這將協助您深入了解及撰寫程式碼。  
  
 加入呼叫以列印，然後您應該已有如下所示的主視窗：  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 如果您按下 F5，則程式碼會在 cmd.exe 視窗中執行，然後您會看見來回擺動的點。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) 中觀看這些指示。  
  
## <a name="see-also"></a>另請參閱  
 [Wiki 文件 (英文)](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTVS 快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

