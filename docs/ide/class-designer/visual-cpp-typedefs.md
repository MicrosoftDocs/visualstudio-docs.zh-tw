---
title: C++類別設計工具中的 typedef
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590692"
---
# <a name="c-typedefs-in-class-designer"></a>C++類別設計工具中的 typedef

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) 陳述式會在名稱及其基礎類型之間建立一或多層間接取值。 **類別設計工具**支援 C++ typedef 類型，其使用 `typedef` 關鍵字進行宣告，例如：

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

## <a name="class-and-struct-shapes"></a>類別和結構圖形

在**類別設計工具**中，C++ typedef 具有 typedef 中指定類型的圖形。 如果來源宣告 `typedef class`，圖形會有圓角和標籤「類別」。 針對 `typedef struct`，圖形會有方角和標籤「結構」。

類別和結構中可宣告巢狀 typedefs。 在**類別設計工具**中，類別和結構圖形可將巢狀 typedef 宣告顯示為巢狀圖形。

Typedef 圖形支援右鍵功能表 (操作功能表) 上的 [顯示為關聯] 和 [顯示為集合關聯] 命令。

### <a name="class-typedef-example"></a>類別 typedef 範例

```cpp
class B {};
typedef B MyB;
```

![類別設計工具中的 C++ 類別 typedef](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>結構 typedef 範例

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![類別設計工具中的 C++ 結構 typedef](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>未命名的 typedef

雖然您可以宣告沒有名稱的 typedef，但**類別設計工具**不會使用您指定的標籤名稱。 **類別設計工具**會使用**類別檢視**產生的名稱。 例如，下列宣告有效，但會以名為 **__unnamed** 的物件形式顯示在 [類別檢視] 和 [類別設計工具] 中：

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **類別設計工具**不會顯示來源類型是函式指標的 typedef。

## <a name="see-also"></a>請參閱

- [使用程式C++代碼](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
