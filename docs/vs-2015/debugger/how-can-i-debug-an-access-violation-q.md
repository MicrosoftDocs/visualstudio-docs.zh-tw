---
title: 如何偵錯存取違規？ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6188cc273cdea1755071e36f606fb8f041508d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297312"
---
# <a name="how-can-i-debug-an-access-violation"></a>如何偵錯存取違規？
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

問題說明  
 我的程式產生存取違規。 該如何偵錯？  
  
## <a name="solution"></a>解決方法  
 如果您在對多個指標取值的程式碼行上取得存取違規，可能很難找出哪個指標造成存取違規。 從 Visual Studio 2015 Update 1 開始，例外狀況對話方塊現在會明確地指出造成存取違規的指標。  
  
 例如，您應該會在下列程式碼中取得存取違規：  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
      ClassC* C;  
      ClassB() {  
            C = new ClassC();  
      }  
     void printHello() {  
            cout << "hello world";  
      }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
    ClassA() {  
            B = nullptr;  
      }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
    A->B->printHello();  
}  
```  
  
 如果您在 Visual Studio 2015 Update 1 中執行這段程式碼，您應該會看到下列例外狀況對話方塊：  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 如果您無法判斷指標造成存取違規的原因，請追蹤整個程式碼，確定已正確指派造成問題的指標。  如果將指標當做參數傳遞，請確定其已正確地傳遞，而且您沒有不小心建立 [淺層複製](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)。 然後確認這些值未在程式中的某處意外變更，方法是為有問題的指標建立資料中斷點，以確定此指標未在程式中的其他位置修改。 如需資料中斷點的詳細資訊，請參閱 [Using Breakpoints](../debugger/using-breakpoints.md)中的＜資料中斷點＞一節。  
  
## <a name="see-also"></a>另請參閱  
 [機器碼偵錯 FAQ](../debugger/debugging-native-code-faqs.md)
