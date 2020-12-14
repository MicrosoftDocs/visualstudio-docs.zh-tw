---
title: 對 c + + 存取違規進行 Debug |Microsoft Docs
description: 當有一個以上的指標是候選時，請參閱疑難排解存取違規的秘訣。 最新版本的 Visual Studio 命名不當指標。
ms.custom: SEO-VS-2020, seodec18
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b0fb7e6f5ae71cf336f9fe206bc7b0208566b615
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398567"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>如何將 c + + 存取違規進行調試

## <a name="problem-description"></a>問題說明

我的程式產生存取違規。 該如何偵錯？

## <a name="solution"></a>解決方案

如果您在對多個指標取值的程式碼行上取得存取違規，可能很難找出哪個指標造成存取違規。 從 Visual Studio 2015 Update 1 開始，例外狀況對話方塊現在會明確地指出造成存取違規的指標。

例如，您應該會在下列程式碼中取得存取違規：

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

如果您在 Visual Studio 2015 Update 1 中執行這段程式碼，您應該會看到下列例外狀況對話方塊：

![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")

如果您無法判斷指標造成存取違規的原因，請追蹤整個程式碼，確定已正確指派造成問題的指標。  如果以參數形式傳遞，請確定其已正確傳遞，且您不會意外地建立 [淺層複製](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)。 然後確認這些值未在程式中的某處意外變更，方法是為有問題的指標建立資料中斷點，以確定此指標未在程式中的其他位置修改。 如需資料中斷點的詳細資訊，請參閱 [Using Breakpoints](../debugger/using-breakpoints.md)中的＜資料中斷點＞一節。

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)