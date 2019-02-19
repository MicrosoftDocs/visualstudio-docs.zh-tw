---
title: PTVS 快速入門：偵錯 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: b636dd4f3a5c5265231898573bfdf52de2dff84e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54834470"
---
# <a name="getting-started-with-ptvs-debugging"></a>PTVS 快速入門：偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 的互動式偵錯工具讓您更容易診斷及解決 Python 程式碼中的問題。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4) 中觀看這些指示。  
  
 在先前的開始使用主題中，您建立空的 Python 應用程式專案，並在 PythonApplication1.py 中輸入下列程式碼：  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 通常當您在 Visual Studio 中使用程式碼時，會按 F5 開始執行您的程式碼。  此命令會建置需要建置的任何專案部分，並開始在偵錯工具執行程式碼。  您可以按 Ctrl + F5 以建置並啟動您的程式碼，而不使用偵錯工具。  使用偵錯工具時，您的程式碼執行速度較慢，但以那樣的成本可以換得很棒的偵錯功能。  
  
 啟動程式碼的另一個方法是使用逐步進入命令 (通常繫結至 F11)。  這就像是 F5 鍵，但它會在每個陳述式暫停執行。  如果您想要在某個時點中斷程式，您可以按程式碼編輯器左邊界中的左指標按鈕，設定中斷點。  當您按下 F5 時，程式的執行會在有中斷點的行中斷或停止。  [偵錯] 功能表有更多逐步執行的選項；比方說，不進入函式呼叫 (F10)、逐步執行函式呼叫 (F11)，或在函式結尾處略過 (shift-F11)。  
  
 還有其他在偵錯工具裡中斷時可以執行的操作。  [區域變數] 視窗會顯示目前的本機變數值。  當您逐步執行程式碼時，會自動更新 [區域變數] 顯示。  [自動變數] 視窗會顯示在執行停止的目前這一行附近的變數。  在 [監看式] 視窗中，您可以輸入任何 Python 運算式，偵錯工具會在每次執行停止時自動更新它。  您也可以將滑鼠指標停留在編輯器視窗中的變數上，如此可看到快顯視窗，其中顯示變數的值，而此資料提示顯示可讓您檢查物件。  某些資料類型有特殊的視覺化檢視，可從資料提示顯示 (例如，具有特殊格式設定的字串，例如 HTML、XML 或 JSON) 存取。  
  
 [呼叫堆疊] 視窗會顯示導致偵錯工具停止處的目前陳述式的擱置中函式呼叫。  您可以選擇跳到不同的堆疊框架 (呼叫堆疊中的程式行)，其中程式碼將會繼續執行每個函式、查詢變數的值等等。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4) 中觀看這些指示。  
  
## <a name="see-also"></a>請參閱  
 [Wiki 文件 (英文)](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [PTVS 快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
