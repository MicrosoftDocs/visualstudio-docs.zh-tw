---
title: 類別設計工具中的 Visual C++ Typedef | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 91bd88938a093f18ea4f83a41de0972daa35bf6c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-typedefs-in-class-designer"></a>類別設計工具中的 Visual C++ Typedef
typedef 陳述式會在名稱與其基礎類型之間建立一或多層間接取值。 類別設計工具支援 C++ typedef 類型，其使用 `typedef` 關鍵字所宣告，例如：  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
您接著可以使用此類型來宣告執行個體︰  
  
`COORD OriginPoint;`  
  
雖然您可以宣告沒有名稱的 typedef，但是類別設計工具不會使用您指定的標籤名稱，而是使用類別檢視所產生的名稱。 例如，下列宣告有效，但會以名為 **__unnamed** 的物件形式顯示在類別檢視和類別設計工具中：  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```

如需使用 `typedef` 型別的詳細資訊，請參閱 [Typedefs](/cpp/aliases-and-typedefs-cpp#typedefs)。

C++ typedef 圖形具有 typedef 中所指定類型的圖形。 例如，如果來源宣告 `typedef class`，則圖形具有圓角和標籤 **Class**。 針對 `typedef struct`，圖形會有方角和標籤「結構」。  
  
類別和結構其內可以宣告巢狀 typedef；因此，類別和結構圖形可以將巢狀 typedef 宣告顯示為巢狀圖形。  
  
Typedef 圖形支援操作功能表上的 [顯示為關聯] 和 [顯示為集合關聯] 命令。  
  
類別設計工具所支援的一些 typdef 類型範例如下︰  
  
`typedef type name`  
  
*name* : *type*  
  
typedef  
  
繪製連接至類型 *name* 的關聯線 (如果可能的話)。  
  
`typedef void (*func)(int)`  
  
`func: void (*)(int)`  
  
typedef  
  
函式指標的 typedef。 未繪製任何關聯線。  
  
如果 typedef 的來源類型是函式指標，則類別設計工具不會顯示 typedef。  
  
```cpp
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
`MyInt: int`  
  
typedef  
  
`A`  
  
類別  
  
繪製從來源類型圖形指向目標類型圖形的關聯線。  
  
`Class B {};`  
  
`typedef B MyB;`  
  
`B`  
  
類別  
  
`MyB : B`  
  
typedef  
  
以滑鼠右鍵按一下 typedef 圖形並按一下 [顯示為關聯] 會顯示 typedef 或類別以及一個聯結兩個圖形的 [別名 -] 行 (與關聯線類似)。  
  
`typedef B MyB;`  
  
`typedef MyB A;`  
  
`MyBar : Bar`  
  
typedef  
  
同上。  
  
```cpp
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
`B`  
  
類別  
  
`MyB : B`  
  
typedef  
  
`A`  
  
類別  
  
`MyB` 是巢狀 typedef 圖形。  
  
`#include <vector>`  
  
`...`  
  
`using namespace std;`  
  
`...`  
  
`typedef vector<int> MyIntVect;`  
  
`vector<T>`類別  
  
`MyIntVect : vector<int>`  
  
typedef  
  
`class B {};`  
  
`typedef B MyB;`  
  
`class A : MyB {};`  
  
`MyB : B`  
  
typedef  
  
-> B  
  
`B`  
  
`A`  
  
類別  
  
-> MyB  
  
類別設計工具不支援使用操作功能表命令來顯示這種關聯性。  
  
`#include <vector>`  
  
`Typedef MyIntVect std::vector<int>;`  
  
`Class MyVect : MyIntVect {};`  
  
`std::vector<T>`  
  
類別  
  
`MyIntVect : std::vector<int>`  
  
typedef  
  
`MyVect`  
  
類別  
  
-> MyIntVect  
  
## <a name="see-also"></a>另請參閱

[使用 Visual C++ 程式碼](working-with-visual-cpp-code.md)  
[Typedefs](/cpp/aliases-and-typedefs-cpp#typedefs)