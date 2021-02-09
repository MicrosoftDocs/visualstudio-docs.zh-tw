---
title: 偵錯工具中的內容運算子 (c + +) |Microsoft Docs
description: 您可能需要為外部範圍內的 c + + 名稱提供內容，並以區功能變數名稱稱隱藏。 瞭解如何使用內容運算子來執行此作業。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 619162bc4237c71c44f960f7ca1e4337a54f3dd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857710"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Visual Studio 偵錯工具中的內容運算子 (c + +) 
您可以使用 C++ 中的內容運算子限定中斷點位置、變數名稱或運算式。 內容運算子對於指定來自外部範圍的名稱相當實用，因為這類名稱會被本機名稱所隱藏。

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> 語法
 指定內容的方式有兩種：

1. {,,[*module*] } *expression*

     大括號必須包含兩個逗號和模組 (可執行檔或 DLL) 名稱或完整路徑。

     例如，若要在 EXAMPLE.dll 的 `SomeFunction` 函式處設定中斷點：

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *module*!*expression*

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *module* 是模組的名稱。 您可以使用完整路徑釐清具有相同名稱的模組。

   如果 *module* 路徑包含逗號、內嵌空格或大括號，您就必須使用引號括住路徑，如此內容剖析器才能正確辨識字串。 單引號會視為 Windows 檔案名稱的一部分，因此您必須使用雙引號。 例如，

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *expression* 是解析為有效目標的任何有效 C++ 運算式，例如 *module* 中的函式名稱、變數名稱或指標位址。

  當運算式評估工具在運算式中遇到符號時，它會依照下列順序搜尋該符號：

1. 語彙範圍向外擴展，從目前區塊開始 (大括號括住的一連串陳述式)，並繼續向外擴展至封閉區塊。 目前區塊是包含目前位置 (指令指標位址) 的程式碼。

2. 函式範圍。 目前函式。

3. 類別範圍 (如果目前位置是在 C++ 成員函式內)。 類別範圍包括所有基底類別。 運算式評估工具將使用一般支配規則。

4. 目前模組中的全域符號。

5. 目前程式中的公用符號。