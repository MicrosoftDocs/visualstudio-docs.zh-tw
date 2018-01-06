---
title: "關於暫存器視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 82d8c547885021d83e272bcd3ab1a5d560c73a39
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="about-the-registers-window-in-visual-studio"></a>關於 Visual Studio 中的暫存器視窗
**註冊**視窗是在已啟用位址層級偵錯時，才可以使用**選項**對話方塊中，**偵錯**節點。  
  
 暫存器是處理器 (CPU) 中的特殊位置，用來儲存處理器正在使用中的小型資料。 編譯或解譯原始程式碼將會根據需要，產生可將資料從記憶體移到暫存器，以及從暫存器移回記憶體的指示。 和存取記憶體內的資料相比，存取暫存器資料的速度非常快，因此允許處理器將資料留在暫存器內並重複存取的程式碼在執行方面，會比需要處理器經常載入與卸載暫存器的程式碼快很多。 為了讓編譯器可以更容易將資料保存於暫存器內，並執行其他的最佳化處理，您應該避免使用全域變數，盡可能使用區域變數。 用這種方式撰寫的程式碼，通常都會具有良好的參考位置。 使用某些語言時 (例如，C/C++)，程式設計人員可宣告一個暫存器變數 (Register Variable)，要求編譯器盡量將該變數保留在暫存器內。 如需詳細資訊，請參閱[Register 關鍵字](http://msdn.microsoft.com/en-us/5b66905a-2f7f-4918-bb55-5e66d4bc50f9)。  
  
 暫存器可分成兩種類型：一般用途和特殊用途。 一般用途的暫存器可包含一般作業的資料，例如將兩個數值相加，或參考陣列中的某個項目。 特殊用途的暫存器具有特定用途和特殊意義。 堆疊指標暫存器就是一個好例子，處理器可用它來追蹤程式的呼叫堆疊。 做為一個程式設計人員，您可能不會直接去使用堆疊指標。 不過，這對於程式的正常運作來說是很重要的，因為若沒有堆疊指標，處理器就不知道在函式呼叫的端點時，該返回何處。  
  
 大部分一般用途的暫存器只會儲存單一資料項目。 例如，單精確度整數、浮點數或陣列的元素。 有些較新的處理器具有較大的暫存器，稱為向量暫存器，它可包含小型的資料陣列。 因為它們可包含許多資料，向量暫存器可讓牽涉到陣列的作業更快地執行。 向量暫存器一開始用於昂貴的高效能超級電腦上，不過現在已可用於微處理器上，以便更有效地處理大量的圖形作業。  
  
 處理器通常擁有兩組一般用途的暫存器，一組適用於浮點作業，另一組則適用於整數作業。 顯而易見地，這些就是浮點和整數暫存器。  
  
 Managed 程式碼會在執行階段編譯為機器碼，以便存取微處理器的實體暫存器。 **註冊**視窗會顯示這些實體的暫存器，通用語言執行平台或原生程式碼。 **註冊**視窗不會顯示暫存器資訊的指令碼或 SQL 應用程式，因為指令碼和 SQL 都是不支援暫存器概念的語言。  
  
 如需有關顯示**註冊**視窗中，請參閱[使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)。  
  
 當您檢視**註冊**視窗中，您會看到項目，例如此範例中：  
  
```  
EAX = 003110D8  
```  
  
 = 號左邊的符號就是暫存器名稱 (在此例中為 EAX)。 = 號右邊的數值代表暫存器的內容。  
  
 **註冊** 視窗可讓您不只是檢視暫存器內容。 當您處於機器碼的中斷模式時，可按一下暫存器的內容，並編輯其數值。 但是您不應該任意進行這個動作。 除非您很了解正在編輯的暫存器和它所包含的資料，否則隨意編輯可能會導致程式損毀或其他不希望得到的結果。 可惜的是，各種 Intel 和 Intel 相容處理器的暫存器組合之詳細資訊不屬於本簡介說明範圍之列。  
  
## <a name="register-groups"></a>暫存器群組  
 若要減少雜亂，**註冊**視窗會將暫存器組織成群組。 如果您以滑鼠右鍵按一下**註冊**視窗中，您會看到包含清單的群組，您可以顯示或隱藏您可視快顯功能表。  
  
## <a name="see-also"></a>請參閱  
 [如何： 使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)