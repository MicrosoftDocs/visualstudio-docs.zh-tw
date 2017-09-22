---
title: "Visual C++ 程式碼片段 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 2
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: b4d0801f9e3924fd801f30b750d0f5dbfca634fd
ms.contentlocale: zh-tw
ms.lasthandoff: 04/05/2017

---
# <a name="visual-c-code-snippets"></a>Visual C++ 程式碼片段
在 Visual Studio 中，您可以使用程式碼片段將常用的程式碼加入您的 C++ 程式碼檔案。 一般而言，您可以用和在 C# 中相同的方式來使用程式碼片段，但是預設程式碼片段的集合不同。  
  
 您可以將程式碼片段加入程式碼中的特定位置 (插入)，或以程式碼片段圍繞某些選取的程式碼。  
  
## <a name="inserting-a-code-snippet"></a>插入程式碼片段  
 若要插入程式碼片段，請開啟 C++ 程式碼檔 (.cpp 或 .h)，在該檔案內部任意處按一下，然後執行下列其中一項動作：  
  
-   按一下滑鼠右鍵以取得操作功能表，然後選取 [插入程式碼片段]  
  
-   在 [編輯/IntelliSense] 功能表中，選取 [插入程式碼片段]  
  
-   使用快速鍵：**CTRL + K + X**  
  
 您應該會看到開頭為 **#if** 的選擇清單。 當您選取 [#if] 時，應該會看到下列程式碼已新增至檔案：  
  
```cpp  
#if 0  
  
#endif // 0  
```  
  
 然後，您就可以使用正確的條件取代 0。  
  
## <a name="using-a-code-snippet-to-surround-selected-code"></a>使用程式碼片段圍繞已選取的程式碼  
 若要使用程式碼片段來圍繞已選取的程式碼，請選取其中一行 (或多行)，然後執行下列其中一項動作：  
  
1.  按一下滑鼠右鍵以取得操作功能表，然後選取 [範圍陳述式]  
  
2.  在 [編輯/IntelliSense] 功能表中，選取 [範圍陳述式]  
  
3.  使用快速鍵：**CTRL + K + S**  
  
 選取 [#if]。 您應該會看到類似下面的內容：  
  
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
 **class** 程式碼片段提供名為 MyClass 的類別定義，這具有適當的預設建構函式和解構函式，其中建構函式和解構函式的定義位於類別之外：  
  
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
  
 Classi 程式碼片段也提供一個名為 MyClass 的類別定義，但是此預設建構函式和解構函式定義於此類別定義之內：  
  
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
  
## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>For 與 foreach 與 forr 與 rfor  
 共有四個不同的 for 程式碼片段，提供不同類型的 for 迴圈。  
  
 **for** 程式碼片段提供一個 `for` 迴圈，其中此條件以物件的長度 (在 `size_t` 中) 為基礎：  
  
```cpp  
for (size_t i = 0; i < length; i++)  
{  
  
}  
```  
  
 **foreach** 程式碼片段提供一個 `for each` 迴圈，這會逐一查看集合的成員：  
  
```cpp  
for each (object var in collection_to_loop)  
{  
  
}  
```  
  
 **forr** 程式碼片段提供一個反向的 `for` 迴圈，其中此條件以物件的長度 (整數) 為基礎：  
  
```cpp  
for (int i = length - 1; i >= 0; i--)  
{  
  
}  
```  
  
 **rfor** 程式碼片段提供一個[範圍架構](/cpp/cpp/range-based-for-statement-cpp)的 for 迴圈 (連結)：  
  
```cpp  
for (auto& i : v)  
{  
  
}  
```  
  
## <a name="the-destructor-snippet-"></a>解構函式程式碼片段 (~)  
 解構函式程式碼片段 (**~**) 會在不同的內容中顯示不同的行為。 如果您將此程式碼片段插入類別時，它會提供該類別的解構函式。 例如，假設有以下的程式碼：  
  
```cpp  
class SomeClass {  
  
};  
```  
  
 如果您插入此解構函式程式碼片段，它就會提供 SomeClass 的解構函式：  
  
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
