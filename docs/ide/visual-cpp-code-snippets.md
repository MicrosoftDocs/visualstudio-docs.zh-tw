---
title: Visual C++ 程式碼片段
description: 瞭解如何使用程式碼片段將常用的程式碼新增至 c + + 程式碼檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: e5cde2be817c49344e02ff06030022f99790a7a2
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478805"
---
# <a name="visual-c-code-snippets"></a>Visual C++ 程式碼片段

在 Visual Studio 中，您可以使用程式碼片段將常用的程式碼加入您的 C++ 程式碼檔案。 一般而言，您可以用和在 C# 中相同的方式來使用程式碼片段，但是預設程式碼片段的集合不同。

您可以將程式碼片段加入程式碼中的特定位置 (插入)，或以程式碼片段圍繞某些選取的程式碼。

## <a name="insert-a-code-snippet"></a>插入程式碼片段

若要插入程式碼片段，請開啟 c + + 程式碼檔 (*.cpp* 或 *.H*) ，按一下檔案內的某個位置，然後執行下列其中一項：

- 按一下滑鼠右鍵以取得操作功能表，然後選取 [插入程式碼片段]

- 在 [編輯/IntelliSense] 功能表中，選取 [插入程式碼片段]

- 使用 **快速鍵： Ctrl** + **K** + **X**

您應該會看到開頭為 **#if** 的選擇清單。 當您選取 [#if] 時，應該會看到下列程式碼已新增至檔案：

```cpp
#if 0

#endif // 0
```

然後，您可以使用正確的條件來取代 **0** 。

## <a name="use-a-code-snippet-to-surround-selected-code"></a>使用程式碼片段圍繞已選取的程式碼

若要使用程式碼片段來圍繞已選取的程式碼，請選取其中一行 (或多行)，然後執行下列其中一項動作：

- 以滑鼠右鍵按一下以取得內容功能表，**然後選取 [** 範圍語句]

- 從 [**編輯**  >  **IntelliSense** ] 功能表中 **Surround With** ，選取 [範圍語句]

- 使用鍵盤，按下： **Ctrl** + **K** + **S**

選取 [#if]。 您應該會看到如下內容：

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

然後，您就可以使用正確的條件取代 0。

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>可以找到 C++ 程式碼片段完整清單的位置

移至 [工具] 功能表上的 [程式碼片段管理員]，並將 [語言] 設定為 [Visual C++]，即可找到 C++ 程式碼片段的完整清單。 在下面的視窗中，展開 [Visual C++]。 您應該會看到所有的 C++ 程式碼片段依照字母順序排列的名稱。

大部分程式碼片段的名稱都一目了然，但某些名稱可能會造成混淆。

## <a name="class-vs-classi"></a>class 與 classi

**class** 程式碼片段提供名為 `MyClass` 的類別定義，這具有適當的預設建構函式和解構函式，其中建構函式和解構函式的定義位於此類別之外：

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

**classi** 程式碼片段也提供一個名為 `MyClass` 的類別定義，但是預設建構函式和解構函式定義於此類別定義內：

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>for 與 forr 與 rfor

共有三個不同的 **for** 程式碼片段，提供不同類型的 `for` 迴圈。

**Rfor** 程式碼片段提供以 [範圍為基礎](/cpp/cpp/range-based-for-statement-cpp)的 for 迴圈 (連結) 。 會優先使用此建構，而非索引式 `for` 迴圈。

```cpp
for (auto& i : v)
{

}
```

**For** 程式碼片段提供 `for` 迴圈，其中的條件是以物件) 中 (的長度為依據 `size_t` 。

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Forr** 程式碼片段提供反向 `for` 迴圈，其中的條件是以物件的整數) 長度 (為基礎。

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>解構函式程式碼片段 (~)

 () 的「函式」程式碼片段會 **~** 在不同的內容中顯示不同的行為。 如果您將此程式碼片段插入類別時，它會提供該類別的解構函式。 例如，假設有以下的程式碼：

```cpp
class SomeClass {

};
```

如果您插入此解構函式程式碼片段，它就會提供 `SomeClass` 的解構函式：

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

如果您嘗試在類別之外插入解構函式程式碼片段，它就會提供解構函式預留位置名稱：

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>另請參閱

- [程式碼片段](../ide/code-snippets.md)